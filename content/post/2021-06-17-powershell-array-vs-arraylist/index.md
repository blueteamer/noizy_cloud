---
title: "PowerShell Array vs. ArrayList"
date: "2021-06-17"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

Like in most programming languages we have several ways to store collections of data in a variable and do awesome stuff with them.

When you're wandering through the internet in most tutorials you will see scripts use an simple array to store data. And they use it for everything.

## Powershell and Arrays

```powershell
$array = @() 
foreach($item in $hughCollection) {
   $array += $item.importantvalue 
}
```

What I want to point out is this

```powershell
$array += $item.importantvalue
```

This is actually the short form of

```powershell
$array = $array + $item.importantvalue
```

That means PowerShell will create a copy of $array and assigns it to a new variable including the new value of $item.importantvalue.

That's ok if it happens once. Even twice is ok. But imagin a loop with hundreds or thousands of entries and in each loop this assignment will happen. I'm sorry for the memory. So what shall we do?

## ArrayList for dynamic assignments

If you need to add values to a collection variable you will be better off with an ArrayList.

An array has a fixed length. Therefore it needs to be destructed and recreated each time you assign a new entry to that variable.

An arraylist has no fixed length and is perfect if you need to gather values in a collection where you don't know the exact amount of entries way before.

```powershell
$arraylist = [System.Collection.ArrayList]@() 
foreach($item in $hughCollection) {
   $arraylist.Add($item.importantvalue)
}
```

This will work way better and also faster. You won't belive me? Try it for yourself.

## Measure time with an array

```powershell
$array = @()
Measure-Command -Expression {@(0..50000).ForEach({$array += $_})}
```

The script creates an array as variable and fills this array within a loop with 50000 entries. Measure-Command monitors the performance and provides an overview at the end.

## Measure time with an array list

```powershell
$arraylist = [System.Collections.ArrayList]@()
Measure-Command -Expression {@(0..50000).ForEach({$arraylist.Add($_)})}
```

Same as the script before - but now we are using an array list.  
You see the difference?

## When to use what?

**Use an array** if you set up a static collection of values which you will iterate through. For example, if you have a fix list of entries you want to process in your script. The values are assigned to the array during the initialization of the variable.

**Use the array** list if you want to gather values throughout a loop or the whole script.

And now... enjoy scripting and stay save!
