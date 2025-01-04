---
title: 'Testing stateful components using Microsoft Pex'
date: 2013-07-23T17:34:00.000-05:00
draft: true
url: 
tags: 
- Microsoft Pex
- Parameterized Unit Tests
- Unit Tests
- Unit testing
---

<\>  
Pattern. This pattern applies for statefull component x that expose members that may transition the state. For each member f(x), one defines a transition type Tf (x; o) which contains a method to invoke f(x) and where o is the test oracle.  
Let us illustrate this pattern with the XmlWriter class from the System.Xml library. This class contains a number of methods (Write...) which have to be called in a particular order to build valid XML documents. The writer also exposes a WriteState property which gives a partial view on the state of the writer:  
```
public abstract class XmlWriter
{
 public abstract void WriteStartElement(string elementName);
 public abstract void WriteEndElement();
 public abstract WriteState WriteState { get; }
}
```  
We start by defining an abstract Transition type that will be used to define each possible transition of the XmlWriter:  
```
public abstract class Transition
{
 public abstract void Execute(XmlWriter writer, XmlWriterOracle oracle);
}
```  
The second parameter of Execute holds a test oracle that will be used to assert additional properties of the writer:  
```
public sealed class XmlWriterOracle
{
 public int ElementDepth = 0;
 public void Invariant()
 {
  PexAssert.IsTrue(this.ElementDepth > -1);
 }
}
```  
For each method in XmlWriter, a transition type inherited from Transition can be defined:  
```
\[DebuggerDisplay("WriteEndElement")\]
public class WriteEndElementTransition : Transition
{
 public override void Execute(XmlWriter writer, XmlWriterOracle oracle)
 {
  writer.WriteEndElement();
  oracle.ElementDepth--;
 }
}
```  
Transitions may also embed assertions and assumptions:  
```
\[DebuggerDisplay("WriteStartElement({Name})")\]
public class WriteStartElementTransition : Transition
{
 public string Name;
 public override void Execute(XmlWriter writer, XmlWriterOracle oracle)
 {
  writer.WriteStartElement(this.Name);
  PexAssert.IsNotNull(this.Name);
  PexAssert.AreEqual(writer.WriteState, WriteState.Element);
  oracle.ElementDepth++;
 }
}
```  
Finally, the parameterized unit test simply takes a sequence of transitions and executes them:  
```
\[PexMethod\]
\[PexUseType(typeof(WriteStartElementTransition))\]
\[PexUseType(typeof(WriteEndElementTransition))\]
public void WriteXml(\[PexAssumeNotNull\]Transition\[\] transitions)
{
 PexAssume.AreElementsNotNull(transitions);
 using (var writer = new StringWriter())
 using (var xwriter = XmlWriter.Create(writer))
 {
  var oracle = new XmlWriterOracle();
  for (int i = 0; i < transitions.Length; ++i)
  {
   var transition = transitions\[i\];
   // apply transition
   transition.Execute(xwriter, oracle);
   // assert invariant still holds
   oracle.Invariant();
  }
 }
}
```  
The assertions and assumptions embedded in the transitions and product code will drive Pex to instantiate different sequence of transitions. The **PexUseTypeAttribute** annotation on the test specify to Pex that those types should be used when a Transition type is needed.