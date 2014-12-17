---
layout: page
title: "Nitrogen Programming Language"
permalink: /nitrogen/
menutitle: Nitrogen
---

Nitrogen is a Lisp-based programming language I created to learn fundamentally how programming languages work. It is not designed to be used in any sort of production environment. It's very minimal, but usable. It's based off the book [Build Your Own Lisp](http://www.buildyourownlisp.com/).

On this page you will be able to find the docmentation for the builtin functions as well as the Standard Library. You'll also find some examples to play with.

You can find the source code for the Nitrogen interpreter at: [github.com/dragonrider23/nitrogen](https://github.com/dragonrider23/nitrogen)

Language Fundamentals
---------------------

Here is where the basics of Nitrogen will be posted.


Language Core
-------------

The following words are reserved keywords for builtin functions or operators, or are used in the core library. This means they cannot be redefined using the (def) or (pdef) functions.

Internal - Functions and Operators

<table>
  <tr>
    <td>load</td>
    <td>print</td>
    <td>error</td>
    <td>exit</td>
    <td>=</td>
    <td>def</td>
  </tr>
  <tr>
    <td>pdef</td>
    <td>undef</td>
    <td>\</td>
    <td>list</td>
    <td>head</td>
    <td>tail</td>
  </tr>
  <tr>
    <td>eval</td>
    <td>join</td>
  </tr>
</table>

Internal - Arithmatic and Comparison Operators

<table>
  <tr>
    <td>+</td>
    <td>-</td>
    <td>*</td>
    <td>/</td>
    <td>if</td>
    <td>==</td>
  </tr>
  <tr>
    <td>!=</td>
    <td>&gt;</td>
    <td>&lt;</td>
    <td>&gt;=</td>
    <td>&lt;=</td>
  </tr>
</table>

Core Library - Language Constructs

<table>
  <tr>
    <td>nil</td>
    <td>true</td>
    <td>false</td>
    <td>pfun</td>
    <td>fun</td>
  </tr>
  <tr>
    <td>do</td>
    <td>not</td>
    <td>or</td>
    <td>and</td>
    <td>++</td>
  </tr>
  <tr>
    <td>--</td>
    <td>select</td>
    <td>case</td>
    <td>otherwise</td>
  </tr>
</table>


Core Library
------------

Core Library - Functions

<table>
  <tr>
    <td>unpack</td>
    <td>pack</td>
    <td>curry</td>
    <td>uncurry</td>
    <td>fst</td>
  </tr>
  <tr>
    <td>snd</td>
    <td>trd</td>
    <td>len</td>
    <td>nth</td>
    <td>last</td>
  </tr>
  <tr>
    <td>map</td>
    <td>filter</td>
    <td>init</td>
    <td>reverse</td>
    <td>foldl</td>
  </tr>
  <tr>
    <td>foldr</td>
    <td>sum</td>
    <td>product</td>
    <td>take</td>
    <td>drop</td>
  </tr>
  <tr>
    <td>split</td>
    <td>take-while</td>
    <td>drop-while</td>
    <td>elem</td>
    <td>lookup</td>
  </tr>
  <tr>
    <td>zip</td>
    <td>unzip</td>
  </tr>
</table>


Standard Library
----------------

This is where you'll eventually find documentation for the Standard Library.


Examples
--------

Here you will find examples of the language in action.
