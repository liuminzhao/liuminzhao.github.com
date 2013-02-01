---
layout: post
title: "java notes"
description: ""
category: 
tags: [java]
---
{% include JB/setup %}

# Eclips #

* `C-1` : quick fix 

# Java #

* `//` as comment 
* `confirm("fisf")`
* `prompt("What is your name?")`, `var = prompt("jkjk")`
* `false` , `5>3`
* comparison, `===`, `>=` , 
* logic: not: `!`,  or `||`
* condition
  
     	  if (100<2) 
		  {
			  statement
		  }
		  else if 
		  {
			  fds
		  }
		  else
		  {
			  statement
		  }

## String ##

	"word".substring(x,y)
	"fdsaf" + "fsdjkfj"
	"AAA".toLowerCase()

## Variable ##

	var varName = data type;
	
## Loop ##

	for (var counter = 1; coutner <=5 ; counter=counter+1)
	{
		statement;
	}
	counter ++ 
	counter +=1

	while (condition) {
		statement;
	}

### loop in obj ###

	for(var property in dog) {
	console.log(property);
	}
	
	dog[prperty];
	
## Functions ##

	var hello=function() {
		return x;
	};

## Array ##

	var lost=[1,3,4] 
	
start from 0

## Switch ##

	switch (jacketColor) {
    
    case "black":
     result = "Pay $300";
    break;
    
    case "brown":
      result = "Pay $200";  
    break;
    
    case "green":
      result = "Pay $5";
    break;
    
    default:
     result = "This color does not match my eyes!";
	 }

## ifelse ##

	result = x > y ? "good job" : 20;

## Math ##

	Math.random()
	Math.floor()
	Math.max()
	Math.PI
	
## Object ##

	var obj={
	  age:22,
	  fdsfa: fsf,
	  speak: function(){
	  }
	}
	
	obj.age
	obj["age"]
	
	var obj= new Object();
	obj.age=24;


can pass objects into functions
	
## Method  ##

	obj.setAge = function(pa){}; 

this

	var setAge=function(x){
		this.age=x;
	}
	bob.setAge=setAge;

## Prototype ##

teach all objects methods:

	className.prototype.newMethod = function() {
	statements; 
	this.name;
	};

Inherit

	Penguin.prototype = new Animal();


## New construct ##
	
	function Person(name, age){
		this.name=name;
		this.age=age;
		this.species="d";
		this.calcArea=function(){
			return this.length*this.width;
		};
	}
	var bob=new Person("bos", 27);
	
## Array of objects ##	

	var family=new Array();
	family[0]= new Person("""");

## function ##

	typeof something;
	
obj method:
	
	obj.hasOwnProperty("name");

## Privacy ##

	function Person(first,last,age) {
	var bankBalance=7500;  # private
	
	  this.getBalance = function() {
      // your code should return the bankBalance
      
    }; # public method
	
	var returnBalance=function(){} ;# private method
	
	}


# Q #

* what is JRE
