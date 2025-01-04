---
title: 'PostgreSQL 101'
date: 2013-06-24T16:59:00.001-05:00
draft: false
url: /2013/06/postgresql-101.html
tags: 
- PostgreSQL
---

PostgreSQL is the finest open source example of the relational database management system (RDBMS) tradition. This means that PostGreSQL is a design-first data store. First you design the schema, and then you enter data that conforms to the definition of that schema.

### History of PostgreSQL

> PostgreSQL has existed in the current project incarnation since 1995, but its roots  
> are considerably older. The original project was written at Berkeley in the early 1970s  
> and called the Interactive Graphics and Retrieval System, or “Ingres” for short. In the  
> 1980s, an improved version was launched post-Ingres—shortened to Postgres. The  
> project ended at Berkeley proper in 1993 but was picked up again by the open source  
> community as Postgres95. It was later renamed to PostgreSQL in 1996 to denote its  
> rather new SQL support and has remained so ever since.

### Installation

You can download the latest PostgreSQL installer from [http://www.postgresql.org/download](http://www.postgresql.org/download) (In this tutorial I’m using the Windows 64bit installer). Setup is straight-forward. Below are screen-shots of installation steps:

[![Setup_2013-06-24_14-23-08](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEimUOWML4h23t3RD_6qHXFB4qE1GzkMQ4uF6fQokNks8oHitkdPp_RZFOpZ1BUErwy8lztZJ6lahFRzBOndecsR0-G4djTC1YsOYocUu7R5PFQ8-T3ZxdQOIVrjNmKWCSszKPkrHq00gw/?imgmax=800 "Setup_2013-06-24_14-23-08")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhYGc_Ytx2AuNfVjs0eTLBXJkTSvxxILuv5Gv7t8oJc4vvDFJNko1I7uM27QhN9_l7BVdk20AAT9rPoE2Bsvv0FoZ4v0oF4oKilgdQMrx6uUpGe7nZln5Yc7T45vnQZGExUlgBYPxNfFg/s1600-h/Setup_2013-06-24_14-23-08%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg5goeC2ZbO7pL3eXKyoj1K2LmcdqVzlqQLBBu130Hg4N8ZUPzIh_gwwTQ66NLe5_Qn654AdcxY1u5Ijn1r9qo4uUg8OSz0DfaN_khqqraa8tVIcPULt1R7cIi1DlgBjrcqveGZLmqrcg/?imgmax=800 "Setup_2013-06-24_14-23-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjMRSjAUtxGZiaraKgcmKHADmHolpwLH7oh2_W0S39SK8J6beecj0oZR2biaGK9kEN4pthksO7XN0aEgI3q9770yTK39bDMBWQ_nvHU_spyzn4QviQk9TPxcaSjYh11Bbh_ItqFcZoyKg/s1600-h/Setup_2013-06-24_14-23-13%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-16](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhw1oMB7kVc9Gc3UD-TFA9oDDAMB6X6TMTggrk1HYt9oMiQxjhKfblM9flsVbaidRcEcoEZPDByw1jQmd8szyWuqFHFs3psZcMRfQmEWhDNuuu0sOdW3M8pPyw68xA2WlF4zc74EAN1YA/?imgmax=800 "Setup_2013-06-24_14-23-16")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg0EY6qPK2xdl60C55T27xHBh8WrfWI4Zdo-0HppsAmD2NcFUkBht13MHj4CpMhD_KRCs8uEeYppXkw_97zLAYU3605EqgLVSA3Jkq7zqBsUHXDZcpcSmVgYhllmSVMQkJZ8I0Qk-IZWg/s1600-h/Setup_2013-06-24_14-23-16%25255B3%25255D.png)

remember the superuser password, you will need it later

[![Setup_2013-06-24_14-23-37](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjvrh44RUwEfXwZQQZ_JXUb9EChvz_IRbo-4quiNUYX-G9pySdsrxKT3sci_9JQM6OSPUHwHZ_mIAgvEXQWL_vnnRwwn0XAElB23FH83X50bH0gE2OdWWU0MIZ0hp3snWwg51GRLGUiYw/?imgmax=800 "Setup_2013-06-24_14-23-37")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhjDEFhtVTkJ2ijwiJNnF0UFe64A4WkcAGFNf5d88zLqmBdTf57wslP0zwrh90R7YwDQhfxeNH_u2_4SPypbRge4zGBGGGK9Ptsjp3SROtX91thUAOb6GZx5XnqlxtLLQVVSfwH1YHRJQ/s1600-h/Setup_2013-06-24_14-23-37%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiqwlyCe8Vev6yQAyq2HD3ZeVwjWz8qNydUrD5X2KE9bubkZfua4eoKDGT8QmB3nMPs8oEnFVTuOJZd8NCAYySpoii80GSAH2vKro8oYZQE5ahn1eytnc2ree8vfGsG2JVBjozpo1jyQA/?imgmax=800 "Setup_2013-06-24_14-23-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwyy-sb4-BYAqEWs5ZE4SeaXbOajrpwqITSL76wCh8hNOVeLhfI7jJgh1tXvCfsHLs_BLyakmpZvPqzoELOTImF4c5UWWFlwqYmGnnLCV7mFOT4BXeTEmTzGM7dzAqBvi9owULbZdCCA/s1600-h/Setup_2013-06-24_14-23-41%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-44](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj4_QjajD_GbygE4W4fDnhfPHmOaZcla09N0eEiI-CPxQrPplh1Q-qcukCXMxzBEyv_HYSmYIZcf0QyW_mSaI-TRgdBnm4mAhB8ls_ckvwSq1kGf9H-aVa2xD2k8GbJIkaMgj59zPKa6w/?imgmax=800 "Setup_2013-06-24_14-23-44")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgfet7zF4SXJrWTJspj1FuBuQBdIfMYfcZ4iiq3Rx2ZCGxA-K-oQ72u1qJxFXix2suE6IjH4knA2uCcYmQLVSy1yKih5KFag-ouPI-zdvei2IqIcMQ5Fa_MD3vkldegpFQ7RflbVAXwog/s1600-h/Setup_2013-06-24_14-23-44%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiDK2KuO8z4Wtpyo6cu6E2LcY3XbSZ-8nX5ZN9Kt-pdlL7-MhhyphenhyphengoGgCUlYM2gxfxVDVjVw6VgnoW5E8GToOwhoYYkhODY1rmqL1x0qk7M0biUPYKyWRuvRgN5Ea6931UrtywJBOTGdlg/?imgmax=800 "Setup_2013-06-24_14-23-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhhWZ97NzbmSGRtyqXJ5HgTmAJvav835lutXyyDshilX3lB1XoNVN80Zsn0ZjnKeJwKSh1s2jA-5KgbY0Odd8K8aHh31nZEVYtCH1dOYinLDDGLePsCHnuVG8_Yui165F88SVlAFD2dJA/s1600-h/Setup_2013-06-24_14-23-47%25255B3%25255D.png)

[![Setup_2013-06-24_14-23-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj3k62drruUZe6KKco8Beq-NLLt5hIsk7Q_0tw-KYhtvQ6DF7DEhKG5Akl3-XeyTDTGURhOgJBaMe2rEa8eOfOWA6oacpzzZZlTq8ebKVM8uQGx60lG7SZQAMhBfjVcNZvDF7G3VSMivg/?imgmax=800 "Setup_2013-06-24_14-23-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEja0fktNnGUlBEATIcO-JCoKKD6_f4Angc1-lVBDF0JJnvw6bNfi8x1n59XGtiYsqKAsvYmU_pB0LrwW-PMAPjmCqbWek9a2vjd723YFh6ku87GkenIl_wTLYuQLIBjCgq7Gf8i8eR8Kw/s1600-h/Setup_2013-06-24_14-23-56%25255B3%25255D.png)

when the PostgreSQL installation finish, you could choose to run Stack Builder to install additional tools. In my case I chose to run Stack builder

[![Setup_2013-06-24_14-25-58](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhg1DDwWLIy29WukvgIEb5mB75b-lt746vv7MEjGJDWlEWxpOs0rt9snz9XJ3gJ4BZZCISakRsgXEByAMGMMf7twnP6ITkNitUnxukO2QQlwVEjNPlKwLxmG1Q4TK1sy-6JludV8K3KIw/?imgmax=800 "Setup_2013-06-24_14-25-58")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh_slvtJck4zP_Rxvhei5Whnd_Mtb-AwIp3iRxA2Y4W5c8ATJArx7WcdI63Je5PbfFBMh3VAX-UvQKAkEcHpk9wdo76oYnN5GSsD6uH-QwohTRtMZ68h1Ykrm9Qoq7J4Ij_asKvHHGwpQ/s1600-h/Setup_2013-06-24_14-25-58%25255B3%25255D.png)

choose your recently installed instance

[![Stack Builder 3.1.0_2013-06-24_14-26-15](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjbRydcMvYvX_F3DqZuMdSSL-LvL_MDuRybQvqZzY0uLHpWBIXGdqgMCuneeV8gc5QybFAfwLUtz9-8cZcKk-lTmncHi0DCkukfrMvbOA0P0C3LokwBRmY4e4-VLCfFctXlfI8RDAiJTQ/?imgmax=800 "Stack Builder 3.1.0_2013-06-24_14-26-15")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh3dHtebl-Z2keU8lBG4HPOpT2Lbw5ga_PnRq1fRyy-sQh34CShQ3Xbc1_a437Ua2ye2FUi74V0xhHrYC8JzCoP26G34-tDAj4JpYFssA-X7AssaOcaJGQKobw6t5La9g71R77sRu8aww/s1600-h/Stack%252520Builder%2525203.1.0_2013-06-24_14-26-15%25255B3%25255D.png)

and I choose to install Npgsql database driver (for future .Net development) and phpPgAdmin for administration tasks.

[![Stack Builder 3.1.0_2013-06-24_14-26-54](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjHuY8YM9SC2ZB3cTZiXNndthbJQ6q8vhEeAirJy2QbwddqKOKcZHnS1QAbe3HmBPbsaPXvJwaGztAZ71Hu8XSl4-ysDYpL6-8pIG8Hmk37xyBQnbevSl68sp3E5FXAI_OsvYnh9NUytA/?imgmax=800 "Stack Builder 3.1.0_2013-06-24_14-26-54")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTv6hoABimGTxVL-imCGIevEo4zS1KVu0eF2P8ec3HNSkxKcMwEjDvQhZKXGoaWpZOK0hO0Epweq9Z51zL0tk_9MxAho4P2VjV8yE3aoVUVhhbAJB-JEAewwXQMmVRxProC9ThQHqTlQ/s1600-h/Stack%252520Builder%2525203.1.0_2013-06-24_14-26-54%25255B3%25255D.png)

[![Stack Builder 3.1.0_2013-06-24_14-27-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiDMqL2I4FflVfZgZ3Fc9LzvidS9uD5at4yrOa1iK8PojEsMxii9t2rOJ4zNe8cqZSuIVMROnHYQ7afUgMMM03wIgmU8p_8iI3okYt96ygHIB1zAat5Gbxl0F7nL3emdh-5Z4uSBvVk8A/?imgmax=800 "Stack Builder 3.1.0_2013-06-24_14-27-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj8Wf1DgKkHejoBPX0hgBafs8zBT77obSMlD3jAdXEu50xhS8Anv93IjP757IA-A9oh8HDPLGQXCsCZLtQ43lj3El3GZgRO0yA5XFrM62898SUp1sTgJ0Wnvzhev1lTWrynCgMHCiE2MA/s1600-h/Stack%252520Builder%2525203.1.0_2013-06-24_14-27-00%25255B3%25255D.png)

[![Stack Builder 3.1.0_2013-06-24_14-27-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhxcU1kQ_ysDKj9tPZhtPDHzYPh98oW2r37FChdeEywh7ErbjCVQ7pZzf-Oj1qUQHS_tjh1iHdeZ4pqLtseWP1Lzd5WK2TGtcZ386yHzU2tatjsmcyKN3U2IR9gre1jyCnkqFWVGwxcew/?imgmax=800 "Stack Builder 3.1.0_2013-06-24_14-27-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhd9rMWbtnqfgqxRiQw0UfPaxr2O-ixUfRRcQmVXmCAExXEYNxLdxdkEZRvq2drymEkBdaW1XfFuKNMmqmlLIFpQe3c2dSeLCcXX-3yCe5M8kSZDxX7lz9QsU8ANlRlNqQ5-uhvu0efoA/s1600-h/Stack%252520Builder%2525203.1.0_2013-06-24_14-27-13%25255B3%25255D.png)

Stack Builder will lunch installation wizards for your chosen tools in sequence

[![Setup_2013-06-24_14-27-30](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhvXYeXE8uGOWMB01i3Inl-3ELiBDejg0a3278_OVpUAWTlQgaOkyT1FnD4e8FXumUd6F0KbixAPakQfrWcID1xZTR5xEXsTmYVwkrOb3slgicy1V0OZWHfIg9TLzQtnhoqQhYuj2jyhA/?imgmax=800 "Setup_2013-06-24_14-27-30")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjyVmliVNsNHLx_1zPSPU0KZsAdqTqL8mb6Rd4bi6W4ZL9EPY-zj7zsA0hFSZJITa7XKedY78WYmqy1lgZ2SZVSRAyV_Y-pdD8rDcHO_uKL90q1sib4JhvRUloU3X5TlOT6zgMUlBPLRw/s1600-h/Setup_2013-06-24_14-27-30%25255B3%25255D.png) 

[![Setup_2013-06-24_14-27-34](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh2eU_wTscgEsDIgVGcCyd_TlC4rU4kDGWFhy-YjR8H8_sXpLX7bI0hdTldP9NHetg9ahFUjD3IHnLh5UBw1oJWcLI_RCGH2BZof7Q707BelMxWmnKwQWLPXJw7QyjSqY-Wnng9suQ8ZA/?imgmax=800 "Setup_2013-06-24_14-27-34")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgzuUH_siLi5iH5E8gxz3V4REJBdUAaUTL1eoU0kl3r8cywCvZMfMz8nxpRu1aidXCKmbr_I9yfTxwp-AjSS6x7c7WCLx3Cml9-kiV3I21nXEm7yUiUs4ONeDFYil7xz5qYuC6TUmg2ZQ/s1600-h/Setup_2013-06-24_14-27-34%25255B3%25255D.png)

[![Setup_2013-06-24_14-27-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEEnkqrVIXj10-j1oBiMS_ltqHEHFwGs2Fm5aqd1d_nMDDdK1zDJwC_pzfokwPF4dOHY_m1JPimkm-I5wQcffdldyKLIiDw_uDFA-mkHt3XfG7ob2WIFG3o1R_Y3McFM2HPb1cd_8lIQ/?imgmax=800 "Setup_2013-06-24_14-27-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfQ1C0uoUlKqWBTtu0XtwJSZg2BA0sbiVDYplzySPS6v7alj70ixWTfgjv38CE6Iin_IG3WIURUob1AGxhxfJJE6k5WQoakz0-i1FMFaHi0n1mMSUXB-oTEdQbQyXhNx96KhboWWs4aQ/s1600-h/Setup_2013-06-24_14-27-36%25255B3%25255D.png)

[![Setup_2013-06-24_14-27-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiqS1NlZzh9hxD5d5ubcYD8G-bAPWDHeJZbAJmNBYChm8exgLXlaMA5bAFV7rghUtWQDncDJPoURDAD0ZEVbRfxec63aYdiq_cnNmcKo6RqJ3PfCKX0ktxrc041emlaD5yXcKBTcyDXDA/?imgmax=800 "Setup_2013-06-24_14-27-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjMaNQN5CypT2K0WtVU5thI1z2fzfL32sFV9GGQYd1UxRkFyj7-a8XH5ksV0NmbOFOb3GuggZITpFpLATSPpwb2SDXZyosW3DIqJoIqeDvPQ02GHEOCCfGjO5oWCiZua5u1p1K0bn3xkQ/s1600-h/Setup_2013-06-24_14-27-41%25255B3%25255D.png)

[![Setup_2013-06-24_14-30-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjA4Qh10hyS2TGXadpsulVm0S1QVWHOoI7Owj5ltyBU3vxMQXjnTgr9kP2SoAsBfLKkQE1QpCusau0XGm9OUtqZ7hc5zBRIADb0UV7KnbMHTsfmBE4ZSDX1-5IWYyM6n6cA21HUwR9wSg/?imgmax=800 "Setup_2013-06-24_14-30-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhVQKMa49jg-EUO0NPXG8PO3YiuOlwtbnMiQtl7aeuumY1YUT0_XEwCC62md1YG-N4Oc8Gh-YDyX3ebyqzSR_j0wtBT7Mj63qwr5TzHaskn_78r5wD5bFAWlCErtfiv7elHx2gpD2i5Rg/s1600-h/Setup_2013-06-24_14-30-25%25255B3%25255D.png)

[![Setup_2013-06-24_14-30-37](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjSEQFV2AvlQmjrcYOuvcRn9_J3moXHp00fpF8X92O0Doh0oVHDAJq0OV7oAhwhARmQT5XXF4nR-G65tT33gljn0bVKx4GCGML-tf8STUclW00A785hxpXxl9fpP0O1IgdfcJH6vYzKsg/?imgmax=800 "Setup_2013-06-24_14-30-37")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjbXhOSDKcNHJn1EEV8Q4MG-LZRhaNwnG2TcDvqInCvpozAQHilyHmrftkWTI0Hn2-E2eNwdqOdKrWWC2hyK8K8JItbFiEogHvd8OFPY4tTSlvZrjZfOhVAVn73KqsHQtdFkakMwE_1FQ/s1600-h/Setup_2013-06-24_14-30-37%25255B3%25255D.png)

[![Setup_2013-06-24_14-30-42](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjlgdOXg50YBydUpxLorZp0AgVhilbwolGDGXF6ckxzZH3_qgEiIqrqY13vNMSQtMpakVyqD-Dt_bLJd9mdWMEi1mZbmQUgv3tne8PAZsrh8vy2SKkftKrhRN1spWpSc2n9Fezx2n6NjQ/?imgmax=800 "Setup_2013-06-24_14-30-42")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjNI8Ws5DAoYmXmC5f3aLHQc8SNJnip65-C8PFSqxZ2ErdSiDriNufXUOnzq6W11ql4gDBhw4YSoL1woWT1cIAQXEo3RjDrElb9uDV3pNlpcaz2MBZY5B6ufU_dGxY40AV1y6-j5BamJw/s1600-h/Setup_2013-06-24_14-30-42%25255B3%25255D.png)

[![Setup_2013-06-24_14-30-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjG6jl6ayzGFdV-UfKfUasbcl9_HNef4z6ypnwkFmI-kUGiH4CKtKhg4iQN1XdBHZp-dXZXH6BZFx-KlbQd9E5cLgxnKYIFMSAqMn8jraBwUd39R_5YvTYcQDOlrkje5fV2BSEj76XW5w/?imgmax=800 "Setup_2013-06-24_14-30-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjDCjRfQTe3VpiIp6Z8ueBsjGghC-w1WSiOw4PomtEkweJovhMzEJEqD5_ZkIDUL9zFGaUNvU3o1nIGRL1RytOx2RLqNjtAKT3D8rT1d-Z-L92MXfWC_VZcWh9PIWBmbo_gUWgB8mwOJA/s1600-h/Setup_2013-06-24_14-30-47%25255B3%25255D.png)

[![Setup_2013-06-24_14-30-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEZ66KYTjKV1sW7s2ZWJMYUlQjv1T6wzx453Y6c9iwxy_GfrE-ghFi_gYCB5_C-kXF1iXTDefA6y1mT5pnyX02HDEy-31mDBnGR_9ItQrfv27srzqqLHB5IZMwW0WcWQ9N4eV6eM6qEQ/?imgmax=800 "Setup_2013-06-24_14-30-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhO89vD4ZBLFFU4ml_zmiUAxuQDAyov1mcSRwfE8odVICkzyT5k0pcRbDRT2w0SKZgzPW0EB-W5A-ZgdHY2fi6NeC8gXBHLqwY1_oeIGuf9aNmz1QtYjBF0LDEuAZt5dDaWu2DgHkNf1Q/s1600-h/Setup_2013-06-24_14-30-53%25255B3%25255D.png)

[![Setup_2013-06-24_14-31-12](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhOlqd-tpbE-Xo1jj2eEW0V4sawrlb1TP3t6eX4VeYsI4BQamMEk-XP0Wp3SLV9stgHTIEuLAmns1HDo3EqJHq0KjZA90t9S82MStLsONXwqWcS7Ct13bJexLJUIrePCBoV1TFF4-hzLQ/?imgmax=800 "Setup_2013-06-24_14-31-12")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhVdyVhvv2AIjnY9jJQR0c6hFVdeckv0nWet9Yof6VuQiofnRRlh8GQsp_EjeJ1DtTNYQ_qresuOp4vqJw8Ax61gGhsxDSb_nJMo0heYHH9M1VBZgfJwD2gQwjfVH65lAQsBgVNHlT-cQ/s1600-h/Setup_2013-06-24_14-31-12%25255B3%25255D.png)

[![Stack Builder 3.1.0_2013-06-24_14-31-19](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiUd7OLYcdW5FmTPZAj3AV8y0u_hSywiqLTLkNNm_WvBKzChrbrJNwxzqInWp7gvXG2MJkzlag2lUAOYKMWbiO6SzoBbsbw3XqBVb5bhSBD1Q-DY1_-bFQVTulKLjtHqHD-3wbG1RER8Q/?imgmax=800 "Stack Builder 3.1.0_2013-06-24_14-31-19")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgw7XeSFd7HHb4vET1ID2xpkWbC4MTyXfn-IwASTrMa2VtUWHtT-nHuVLgkYz2pO35rkBFOrCLCdoNu-fBSryCVyPxKSuktAzk1JU45tBYuJIQiZTNHRZAP2uCvYudnD9w8CQQy9a5Eqg/s1600-h/Stack%252520Builder%2525203.1.0_2013-06-24_14-31-19%25255B3%25255D.png)

### Starting with PostgreSQL

To get started, open _**pgAdmin III**_ from your start menu. On the left hand side right-click on your server instance and click _Connect_

[![pgAdmin III_2013-06-24_15-08-22](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjIUR76YAGD7hX92cdznvz4VpDzuiLsmR4A5SPk5qwlXyQ0QeaSJm7Twf6f3b8doqTTL1CoS7kmVUKDwvNCFyOHJPxZVmEweN2bYzzbfH0REY8aQsgO-0rYcAZuPQDNDBHs2-eDHbvkow/?imgmax=800 "pgAdmin III_2013-06-24_15-08-22")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1ln6042HuoZJjqS0uwseZmK0Pwz1ksV5vUHFZtyFJqhaFf4y-WDG1qQVvE4HtnvfRQKqEOWzDgLMeq0ezdEptByvBYf5bvlhS1pxVlg5tmcwFXY_qMSfraB8t47Y6igU-hep92wLb_w/s1600-h/pgAdmin%252520III_2013-06-24_15-08-22%25255B3%25255D.png) 

enter the password you used in the setup

[![Connect to Server_2013-06-24_15-08-43](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj0REUTUCfpI3dORXaSth8ayn0l7vogfP5AbUHBhpQra29QKt2pEXx46cFjezYowxfpGgRHeIaeQNGBHGnOjZQmpxFNQNlJyPhoTWXV9kk9LQrpnmYCi4b4mlDI6oviNqGu1RsZG960uQ/?imgmax=800 "Connect to Server_2013-06-24_15-08-43")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjHgcWY_l8bt70Q2bhC23IPjjgUxSWw136kjquZ1fisWNQOVQxhRjEQAQcF3X_7Q_aGbPKmaYKef1rrqNJkgNx8QAawGfM83VOJHVTb28VgZFGWH_8aZO19yaLSanCtyUFcE12mkawrzQ/s1600-h/Connect%252520to%252520Server_2013-06-24_15-08-43%25255B6%25255D.png)

Once you connected to your server, you can right click on the databases node and click _New Database_

[![pgAdmin III_2013-06-24_15-09-33](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjv61Q0bZ8k9wyvyDdACfdzZgpKzCUbHOnIyn-K0mNcLTaFIXqLc9Qimz6LFIGjiSuYkDZwLBCde9rzHXas3QME68IR1peuunhQlF-lem2gX4X77kbhVknjfAzD3IByzQbgJWvrkIW6JQ/?imgmax=800 "pgAdmin III_2013-06-24_15-09-33")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEggGs1hpEYrhN7oA79l2MBfmjBKILZCUofD-mWCycAoj2sT8unAC4OLhjbDhbpMYLtXYHXzzHHze7W9Nc666W9fOFNKh-HNZq9nPNB4UZiMpgXFPeunkjPZvQVFzxXlXKnsr_9rxhksfQ/s1600-h/pgAdmin%252520III_2013-06-24_15-09-33%25255B3%25255D.png)

we going to create a simple database called _book_ with the default settings

[![New Database..._2013-06-24_16-45-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiWfyICaUIps6rzOLeOz1cZVbHerxJKK6CfA80MUkFFCgOE82qQnd8yageBeYU9MceVjCggY8C8j8lIhVDAzEtrux8DDxKgYKx2PJKk41BXmydgcRTux8Zauo02O_7C4YNnzI5F5z_wZg/?imgmax=800 "New Database..._2013-06-24_16-45-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjbloJ5bxdbZN_zTiVW95B37hx1XBuTFTt0gjzOeZzE3IuZKk3gjixRiCRc0Dr8bIiFTQ5V4IVMxsSv8cIWV0ZQG3dKk3-YUrxAPDGMsSW8RyDj9uL9EpMN73whjbZttLY1QOFzw_vXZQ/s1600-h/New%252520Database..._2013-06-24_16-45-31%25255B3%25255D.png)

to start writing queries, you could open _Tools_ menu, then click _Query Tool_ (or press CTRL + E).

### Working with Tables

Creating a table consists of giving it a name and a list of columns with types  
and (optional) constraint information. Each table should also nominate a  
unique identifier column to pinpoint specific rows. That identifier is called a  
PRIMARY KEY. The SQL to create a countries table looks like this:

```
CREATE TABLE countries (country\_code char(2) PRIMARY KEY,country\_name text UNIQUE);  
  

```  

copy and paste this code in the Query Tool and click [![Query - book on postgres@localhost5432 _2013-06-24_16-54-24](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiOSpOHBncGOon6aohDW06JJSeBjC3Q8Oycq4Q20ZzX-MkQ4S3UZtMtYqBapE4E8niMiH2Anb5G-f5z6FQhGdwSkFFT8S4FTyOIVfr-CQ-iPmJgCvMZEK5IvwSOi1norGSJ9aG7dW5jdg/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-24_16-54-24")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiMpSO8ySYAidXj4ckezmLdc8hWsp4anameXu0yLs0RU0LrKypbRAiB_pmEw6Ft60lMdXDXTb__AVh0JU_6M-RwkCzu_-jFkSTo9nOtXMPHC54XE8PyhbC3H7Z7PoW9GIAPCAe8tyzDA/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-24_16-54-24%25255B2%25255D.png) on the toolbar to run it.

  

To insert values in our countries table:

```
INSERT INTO countries (country\_code, country\_name)  
VALUES ('us','United States'), ('mx','Mexico'), ('au','Australia'),  
('uk','United Kingdom'), ('de','Germany'), ('ll','Loompaland');  
  

```  

To select from our table:

```
SELECT \* FROM countries;  
  

```  

To delete :

```
DELETE FROM countries  
WHERE country\_code = 'll';  

```  

Now, let’s add a cities table. To ensure any inserted country\_code also exists in our countries table, we add the REFERENCES keyword. Since the country\_code column references another table’s key, it’s known as the foreign key constraint.

```
CREATE TABLE cities (  
name text NOT NULL,  
postal\_code varchar(9) CHECK (postal\_code <> ''),  
country\_code char(2) REFERENCES countries,  
PRIMARY KEY (country\_code, postal\_code)  
);  

```  

we constrained the name in cities by disallowing NULL values. We constrained postal\_code by checking that no values are empty strings (<> means not equal). Furthermore, since a PRIMARY KEY uniquely identifies a row, we created a compound key: country\_code + postal\_code. Together, they uniquely define a row. now if you try to run this code you will get an error because we violating referential integrity:

```
INSERT INTO cities  
VALUES ('Toronto','M4C1B5','ca');  

```  

To update records:

```
INSERT INTO cities  
VALUES ('Portland','87200','us');  
UPDATE cities  
SET postal\_code = '97205'  
WHERE name = 'Portland';  

```  

### Inner Join

  

Being a relational database gives PostgreSQL the ability to join tables together when reading them. Joining, in essence, is an operation taking two separate tables and combining them in some way to return a single table. It’s somewhat like shuffling up Scrabble pieces from existing words to make new words. The basic form of a join is the inner join. In the simplest form, you specify two columns (one from each table) to match by, using the ON keyword.

```
SELECT cities.\*, country\_name  
FROM cities INNER JOIN countries  
ON cities.country\_code = countries.country\_code;  

```  

[![Query - book on postgres@localhost5432 _2013-06-25_09-07-07](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjuoTx-0s2R0e-Zl3elXFmPdvuRAi22bPbfg5lPPfq1lM_CAHB5C9HBDfV01tYK9RB1vTHFRlOAH-Ievz-csB6gELrTiiFG9n0uXHKrSSjQTTiqlzoeS5LYG9tS6iNe5AfhyphenhyphentvjG2tGjQ/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_09-07-07")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhowPfd7rt82E5b14jf-3j-R9L1GXYU78WOG4QLCJsdYTMpp-uj6seuYOUmo5upr9sQD05T4VKboOFsGu0lrT3LctE7nd-yUNtOiRiIpJ0UGTI97hdLH5bi2O8BwktzG4X2uFMc6qCDCA/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_09-07-07%25255B3%25255D.png)

  

The join returns a single table, sharing all columns’ values of the cities table plus the matching country\_name value from the countries table. We can also join a table like cities that has a compound primary key. To test a compound join, let’s create a new table that stores a list of venues. A venue exists in both a postal code and a specific country. The foreign key must be two columns that reference both cities primary key columns. (MATCH FULL is a constraint that ensures either both values exist or both are NULL.)

```
CREATE TABLE venues (  
venue\_id SERIAL PRIMARY KEY,  
name varchar(255),  
street\_address text,  
type char(7) CHECK ( type in ('public','private') ) DEFAULT 'public',  
postal\_code varchar(9),  
country\_code char(2),  
FOREIGN KEY (country\_code, postal\_code)  
REFERENCES cities (country\_code, postal\_code) MATCH FULL  
);  

```  

This venue\_id column is a common primary key setup: automatically incremented integers (1, 2, 3, 4, and so on…). Creating new row will populate this column automatically. We make this identifier using the SERIAL keyword. CHECK keyword check that a column supplied value against a set of predefined values. DEFAULT provide a default value to be inserted in case user supplied nothing.

```
INSERT INTO venues (name, postal\_code, country\_code)  
VALUES ('Crystal Ballroom', '97205', 'us');  

```  

Joining the venues table with the cities table requires both foreign key columns.

```
SELECT venues.venue\_id, venues.name, cities.name  
FROM venues INNER JOIN cities   
ON venues.postal\_code = cities.postal\_code AND venues.country\_code = cities.country\_code;  

```  

[![Query - book on postgres@localhost5432 _2013-06-25_11-03-08](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgNoCf2pP67ZGoVzWWPv1iGPpt-CFvQ781uecx0_jUdywgtVu2a9ZimLv58UKm3rrSdmyaukJkR5et5JS87vJY6CCWlGgjMvT8OEjsrS-ovGx32xA7AKM-idw683HzMVC1NBuHjgWc28w/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_11-03-08")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi9HNFjXKwlyN5emTRag84m2TC0TZI10Jt98wJeVKHofkb0ezX1dwMjbmsSyHGMoNpYdn0uOXJGQ-IULhx_YRfT9xa474AJuHxeCdooE7OueJYknzsNWHVabIkIHFuc7UOqMjNAOPCbXw/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_11-03-08%25255B5%25255D.png)

  

### Outer Join

  

Outer joins are a way of merging two tables when the results of one table must always be returned, whether or not any matching column values exist on the other table. Let's create a table and populate it for testing this:

```
CREATE TABLE events (  
event\_id SERIAL PRIMARY KEY,  
title varchar(255),  
starts timestamp,  
ends timestamp,  
venue\_id integer,  
FOREIGN KEY (venue\_id)  
REFERENCES venues (venue\_id) MATCH FULL  
);  
  
INSERT INTO events (title, starts, ends, venue\_id)  
VALUES ('LARP Club', '2012-02-15 17:30:00', '2012-02-15 19:30:00', 1);  
INSERT INTO events (title, starts, ends)  
VALUES ('April Fools Day', '2012-04-01 00:00:00', '22012-04-01 23:59:00');  
INSERT INTO events (title, starts, ends)  
VALUES ('Christmas Day', '2012-12-25 00:00:00', '2012-04-01 23:59:00');  

```  

Now the results of the following two queries showing you the difference between INNER JOIN and OUTER JOIN.

```
SELECT events.title, venues.name  
FROM events JOIN venues  
ON events.venue\_id = venues.venue\_id;  
  
SELECT events.title, venues.name  
FROM events LEFT JOIN venues  
ON events.venue\_id = venues.venue\_id;  

```  

Finally, there’s the FULL JOIN, which is the union of LEFT and RIGHT; you’re guaranteed all values from each table, joined wherever columns match.

  

### Indexes

  

RDBMSs uses indexes to reducing disk reads and query optimization (among other things). If we select the title of Christmas Day from the events table, the algorithm must scan every row for a match to return. Without an index, each row must be read from disk to know whether a query should return it. An index is a special data structure built to avoid a full table scan when performing a query. PostgreSQL (like any other RDBMS) automatically creates an index on the primary key, where the key is the primary key value and where the value points to a row on disk. Using the UNIQUE keyword is another way to force an index on a table column. PostgreSQL also creates indexes for columns targeted by FOREIGN KEY constraint.

  

You can explicitly add a hash index using the CREATE INDEX command, where each value must be unique. _btree_ is the suitable data structure for ranges. For more information, refer to [online documentation](http://www.postgresql.org/docs/9.1/static/sql-createindex.html).

```
CREATE INDEX events\_starts  
ON events USING btree (starts);  

```  

### Aggregate Functions

  

An aggregate query groups results from several rows by some common criteria. It can be as simple as counting the number of rows in a table or calculating the average of some numerical column. Examples:

```
SELECT count(title)  
FROM events  
  
SELECT min(starts), max(ends)  
FROM events  

```  

Aggregate functions are useful but limited on their own. If we wanted to count all events at each venue, we could write the following for each venue ID (which is tedious):

```
SELECT count(\*) FROM events WHERE venue\_id = 1;  
SELECT count(\*) FROM events WHERE venue\_id = 2;  
SELECT count(\*) FROM events WHERE venue\_id = 3;  
SELECT count(\*) FROM events WHERE venue\_id IS NULL;  

```  

### Grouping

  

With GROUP BY, you tell Postgres to place the rows into groups and then perform some aggregate function (such as count()) on those groups.

```
SELECT venue\_id, count(\*)  
FROM events  
GROUP BY venue\_id;  

```  

[![Query - book on postgres@localhost5432 _2013-06-25_13-49-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhfT24gH8VvOU6re6U8GYi_gjha0yA3rFIOzaXU-KiJ4Pra8DxOd93oQ0XwJtv_Y3Mdkb4rE407eIv8SBPaZHW16nymb-HHsX2NxNR7Byc8a8us9jSCy72VTDzJntd-5avXHeGty1lGfA/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_13-49-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh3Kc6EYsgQgZvyM04VCVv2Kmw1akzoSuAnxAnPqYXA0SR3eWP5X3Y_moJwAobl8TmMUedq5Usj7csGxMZc4fzk_wr8VDxCyWnh2H_K-19x7jgF3oJbhSXHzo6Y6Szw2_Y2GR3_OkrzsA/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_13-49-47%25255B3%25255D.png)

  

The GROUP BY condition has its own filter keyword: HAVING. HAVING is like the WHERE clause, except it can filter by aggregate functions (whereas WHERE cannot).

```
SELECT venue\_id  
FROM events  
GROUP BY venue\_id  
HAVING count(\*) = 1;  

```  

[![Query - book on postgres@localhost5432 _2013-06-25_13-50-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglndaMdqiFOF3V77UeultaDHDOS2NvdWrsfdL3FS6Y4yCqcpp6JJJyIr2bjNMzgNGLubWHCJTktgivrSwO55MM5vZJuQZ8F10utu4KPm6n_t00Re3lKV_YnDot9w_MJ7O66biK-r0KnQ/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_13-50-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhcdv4hJQ140tSDQ6A_hKaDJEAujFy8lZ7CwTDnVXVU6R11bla4e40UIjlrw4zxaY-cSL-OSJQ7UlUaF3zLWS59uV0i_gMUjkERoKu_s2Mu8Ws2CsH4aMYlUHGbu9XxXIE8UewrJ_o4ew/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_13-50-56%25255B2%25255D.png)

  

You can use GROUP BY without any aggregate functions. If you SELECT one column, you get all unique values.  
SELECT venue\_id FROM events GROUP BY venue\_id;  
This kind of grouping is so common that SQL has a shortcut in the DISTINCT keyword.  
SELECT DISTINCT venue\_id FROM events;  
The results of both queries will be identical.

  

### Window Functions

  

Window functions are similar to GROUP BY queries in that they allow you to run aggregate functions across multiple rows. The difference is that they allow you to use built-in aggregate functions without requiring every single field to be grouped to a single row. If we attempt to select the title column without grouping by it, we can expect an error.

  

[![Query - book on postgres@localhost5432 _2013-06-25_14-10-42](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKH9a7eBX6s0D9h9JasaiyEkMbJE9SXSZYwTtJAulYD-_hKe-XuwZLkPxZwoU4YsGn9yyblGDy85HCoE7xsKDJNdLwqNbNFWPt7EABmRWxehV43KHOh34dQUG10qergL8bcC8g28_5Xg/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_14-10-42")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi9zXSdVPo6QEZWQgG4BI__rZuGwPsnByFNeBCU0sdfnQflQEGDWyvbhPauwSZIrcf6Xw1tx9-o58E2op5FamZsG-SMi-WEVUXKK7FMTvdKCN0Yv9ttxXBlJbwfWsm-mdQlTpbKVrjcbw/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_14-10-42%25255B3%25255D.png)

  

We are counting up the rows by venue\_id, and in the case of LARP Club and Wedding, we have two titles for a single venue\_id. Postgres doesn’t know which title to display. Whereas a GROUP BY clause will return one record per matching group value, a window function can return a separate record for each row. Window functions return all matches and replicate the results of any aggregate function. It returns the results of an aggregate function OVER a PARTI TI ON of the result set.

  

[![Query - book on postgres@localhost5432 _2013-06-25_14-17-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgKWmTkxg1XfYJJzUn7gO8mYKDenwk_Gbl9zBFdekwlnfG9OhE_WkgqV2bZ0WkahaAvO8jGCOKUOZdXmXr6MvGxfgOd8-GwQwg6106Lwle4TXT9U7jIhFPSgPh1ad0GPHxArlVN4eceTQ/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_14-17-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjHcG_J59nC6rWXkpNZCWr1mXw2v8ePqC9qz_YN21yCgEEt47P4AuUdziEOw8WsNEaLDCtaG7h4zfSRTnYaMYNtYaVKwZxHENP6rNxuaWQBxu0sHFBGAz2dZDuFwb86zzcL9yFxKQB4mg/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_14-17-36%25255B3%25255D.png)

  

### Transactions

  

Transactions ensure that every command of a set is executed. If anything fails along the way, all of the commands are rolled back like they never happened. It’s the _all or nothing_ motto that gives relational databases its consistency capability.

  

PostgreSQL transactions follow ACID compliance, which stands for **A**tomic (all ops succeed or none do), **C**onsistent (the data will always be in a good state—no inconsistent states), **I**solated (transactions don’t interfere), and **D**urable (a committed transaction is safe, even after a server crash). Transactions are useful when you’re modifying two tables that you don’t want out of sync.

  

We can wrap any transaction within a BEGIN TRANSACTION block. To verify atomicity, we’ll kill the transaction with the ROLLBACK command.

  

### Stored Procedures

  

Every command we’ve seen until now has been declarative (executed on the client side), but you can execute code on the database side also. Example of a stored procedure and how to run it:

```
CREATE OR REPLACE FUNCTION add\_event( title text, starts timestamp,  
ends timestamp, venue text, postal varchar(9), country char(2) )  
RETURNS boolean AS $$  
DECLARE  
did\_insert boolean := false;  
found\_count integer;  
the\_venue\_id integer;  
BEGIN  
SELECT venue\_id INTO the\_venue\_id  
FROM venues v  
WHERE v.postal\_code=postal AND v.country\_code=country AND v.name ILIKE venue  
LIMIT 1;  
IF the\_venue\_id IS NULL THEN  
INSERT INTO venues (name, postal\_code, country\_code)  
VALUES (venue, postal, country)  
RETURNING venue\_id INTO the\_venue\_id;  
did\_insert := true;  
END IF;  
\-- Note: not an “error”, as in some programming languages  
RAISE NOTICE 'Venue found %', the\_venue\_id;  
INSERT INTO events (title, starts, ends, venue\_id)  
VALUES (title, starts, ends, the\_venue\_id);  
RETURN did\_insert;  
END;  
$$ LANGUAGE plpgsql;  
  
SELECT add\_event('House Party', '2012-05-03 23:00',  
'2012-05-04 02:00', 'Run''s House', '97205', 'us');  

```  

### Triggers

  

Triggers automatically fire stored procedures when some event happens, like an insert or update. They allow the database to enforce some required behavior in response to changing data.

  

Let's create a function that logs any event changes into logs table. First we create the table

```
CREATE TABLE logs (  
event\_id integer,  
old\_title varchar(255),  
old\_starts timestamp,  
old\_ends timestamp,  
logged\_at timestamp DEFAULT current\_timestamp  
);  

```  

Next, we build a function to insert old data into the log. The OLD variable represents the row about to be changed (NEW represents an incoming row, which we’ll see in action soon enough). Output a notice to the console with the event\_id before returning. Then we create our trigger to log changes after any row is updated through this function.

```
CREATE OR REPLACE FUNCTION log\_event() RETURNS trigger AS $$  
DECLARE  
BEGIN  
INSERT INTO logs (event\_id, old\_title, old\_starts, old\_ends)  
VALUES (OLD.event\_id, OLD.title, OLD.starts, OLD.ends);  
RAISE NOTICE 'Someone just changed event #%', OLD.event\_id;  
RETURN NEW;  
END;  
$$ LANGUAGE plpgsql;  
  
CREATE TRIGGER log\_events  
AFTER UPDATE ON events  
FOR EACH ROW EXECUTE PROCEDURE log\_event();  

```  

To test our trigger let's update an event and see the trigger output:

  

[![Query - book on postgres@localhost5432 _2013-06-25_15-58-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhkjpk2hoecB-y_RfAQ4_dzxdZiOjR2NSM-tpZm5FY6utzD_kxWbpzYU2Age9yVioikwnOVjw8wF1OrIpEy8bNDe3aImF-TYSo6nKka7hWjYGF80CCCUzNm5fpP7W-SNvloyUWu1LeKlw/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_15-58-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgpIn9h0wn-oVOJ_Tk3hz2zVVgMmboCZhhv3dxAPJWMcaKuu4_oddz43yniHXl2DohUI1B5ZM4-4o-cCfBr2nV3hyphenhyphenoWvzdu1AfRbtpf3uqTuX6YgKZ95RDkX3FxegvPozxdcarFxDtLTQ/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_15-58-53%25255B3%25255D.png)

  

and the old event was logged

  

[![Query - book on postgres@localhost5432 _2013-06-25_16-00-49](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjau35gduGK9u0f61An_uie_K2IZyqLj1wmlKvbq4GCC8cas7CXTeIbz6tRfL96E9xFZA8PQROZQ-3IvUB3lL-zKItRg9PMEBg7sEwrI4Sp6tYU07v-N5rgB8yyf0BUrmGAz73l-uPINg/?imgmax=800 "Query - book on postgres@localhost5432 _2013-06-25_16-00-49")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgz1TrcBveQqgOp4XbZYeaW0izcMDE5K1jhucDel9SzQopYQHMO1u1vVG5d1ZsNXTQ7BVj5il-DXrphIjhpjAmg6-XhJzepamD3It0ckGZHf8czw4kIuh3PX-AZupk0yaUHhPVwcjFR6Q/s1600-h/Query%252520-%252520book%252520on%252520postgres%252540localhost5432%252520_2013-06-25_16-00-49%25255B3%25255D.png)

  

### Views

  

Views are aliased queries that can be queried by its alias like any other table. Creating a view is as simple as writing a query and prefixing it with CREATE VIEW some\_view\_name AS. Views are good for opening up complex queried data in a simple way. If you want to add a new column to the view, it will have to come from the underlying table.

```
CREATE VIEW holidays AS  
SELECT event\_id AS holiday\_id, title AS name, starts AS date  
FROM events  
WHERE title LIKE '%Day%' AND venue\_id IS NULL;  
  
SELECT name, to\_char(date, 'Month DD, YYYY') AS date  
FROM holidays  
WHERE date <= '2012-04-01';  

```  

### The RULE system

  

The rule system (more precisely speaking, the query rewrite rule system) is totally different from stored procedures and triggers. It modifies queries to take rules into consideration, and then passes the modified query to the query planner for planning and execution. More information can be found [here](http://www.postgresql.org/docs/8.2/static/rules.html). Example of changing query to allow updating our holidays view:

```
CREATE RULE update\_holidays AS ON UPDATE TO holidays DO INSTEAD  
UPDATE events  
SET title = NEW.name,  
starts = NEW.date  
WHERE title = OLD.name;  
  
UPDATE holidays SET date = '6/25/2013' where name = 'Christmas Day';  

```  

### Crosstab

```
crosstab(text source\_sql, text category\_sql) takes two queries to pivot results on one of them on the results of the other. 
```  

  
*   _source\_sql_ is a SQL statement that produces the source set of data. This statement must return one row\_name column, one category column, and one value column. It may also have one or more "extra" columns. The row\_name column must be first. The category and value columns must be the last two columns, in that order.  
    
*   _category\_sql_ is a SQL statement that produces the set of categories. This statement must return only one column. It must produce at least one row, or an error will be generated. Also, it must not produce duplicate values, or an error will be generated.

  

If this is the first time you use something from the [tablefunc module](http://www.postgresql.org/docs/current/interactive/tablefunc.html), you may need to install it to your database by running `CREATE EXTENSION tablefunc;`

```
create table sales(year int, month int, qty int);  
insert into sales values(2007, 1, 1000);  
insert into sales values(2007, 2, 1500);  
insert into sales values(2007, 7, 500);  
insert into sales values(2007, 11, 1500);  
insert into sales values(2007, 12, 2000);  
insert into sales values(2008, 1, 1000);  
  
select \* from crosstab(  
  'select year, month, qty from sales order by 1',  
  'select m from generate\_series(1,12) m'  
) as (  
  year int,  
  "Jan" int,  
  "Feb" int,  
  "Mar" int,  
  "Apr" int,  
  "May" int,  
  "Jun" int,  
  "Jul" int,  
  "Aug" int,  
  "Sep" int,  
  "Oct" int,  
  "Nov" int,  
  "Dec" int  
);  

```  

### Full-Text Search

  

Full-text search enables the user to search text columns with parts of the column value, not the exact value like in regular queries.

  

  
*   **LIKE and ILIKE** : LIKE and ILIKE (case-insensitive LIKE) are the simplest forms of text search. LIKE compares column values against a given pattern string. The % and \_ characters are wildcards. % matches any number of any characters, and \_ matches exactly one character.  
    
      
    *   SELECT title FROM movies WHERE title ILIKE 'stardust%';  
          
        *   will return movies with titles like : “Stardust” or “Stardust Memories”
    
      
    
*   **Regex** : You could write the WHERE part of your queries against text columns in regular expressions. A regular expression match is led by the ~ operator, with the  
    optional ! (meaning, not matching) and \* (meaning case insensitive). So, to count all movies that do not begin with the, the following case-insensitive query will work. The characters inside the string are the regular expression.  
    
      
    *   SELECT COUNT(\*) FROM movies WHERE title !~\* '^the.\*';
    
      
    
*   **Bride of Levenshtein** : Levenshtein is a string comparison algorithm that compares how similar two strings are by how many steps are required to change one string into another. Each replaced, missing, or added character counts as a step (Changes in case cost a point too). The distance is the total number of steps away. levenshtein() function is provided by the fuzzystrmatch contrib package.The following query return 3 because we need to replace 2 characters and and add 1 character to make bat into fads.  
    
      
    *   SELECT levenshtein('bat', 'fads');
    
      
    
*   **Trigram** :  A trigram is a group of three consecutive characters taken from a string. The pg\_trgm contrib module breaks a string into as many trigrams as it can. Finding a matching string is as simple as counting the number of matching trigrams. The strings with the most matches are the most similar. It’s useful for doing a search where you’re OK with either slight misspellings or even minor words missing. The longer the string, the more trigrams and the more likely a match.  
    
      
    *   SELECT show\_trgm('Avatar');  -- returns {" a"," av","ar ",ata,ava,tar,vat}
    
      
    
*   PostgreSQL have more natural language processing capabilities (**TSVector** and **TSQuery**) and even can search by word phonetics (**metaphone**)  
    
*   You could combine text search function in many interesting ways like the following query that “Get me names that sound the most like Robi n Williams, in order.”  
      
    *   SELECT \* FROM actors  
        WHERE metaphone(name,8) % metaphone('Robin Williams',8)  
        ORDER BY levenshtein(lower('Robin Williams'), lower(name));

  

  

In this post we introduced PostgreSQL, a popular open source RDBMS. In future posts we will introduce more DBMSs.