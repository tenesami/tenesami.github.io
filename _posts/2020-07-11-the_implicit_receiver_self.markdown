---
layout: post
title:      "The implicit receiver (self)"
date:       2020-07-11 21:05:56 -0400
permalink:  the_implicit_receiver_self
---


Before I start explaining about self, let us define what implicit mean. The Mariam Webster dictionary defines implicit as “capable of being understood from something else though unexpressed: implied an implicit assumption.” So what does it mean implicit receiver ? Hang on I will explain it soon, before that lets talk about object and how ruby communicate with objects. 

Since ruby is pure object-oriented programing language, in ruby every thing is an object, literally everything: class, method, string, variable, boolean you name it. You may ask what does self anything to do with object? Yes it does, the one and only one way ruby communicates with object is by calling method. In the process of calling method, if we didn’t specify the receiver we implicitly assume self is the implicit receiver. Then we may ask again, what is self? as instructor Howard put it  “self is the instance inside instance method i.e the instance used to call the method   self is the class, inside the class method i.e the class used to call the method.” 

Example

			class Album
 				@@album_count = 0  
 
 				def self.count               
   					@@album_count   
				end					  	
			end

The method self.count is know as the class method. Here self used as the implicit receiver of the class that count the data stored in the class variable. To call the class method self.count you will use the Album class (Album.count)

Example
	class Album
			attr_accessor :name

    			@@album_count = 1

		def self.count               
   			@@album_count   
		end	

    		def initialize(name)
        		self.name = name
    		end

    		def intro
        		"Hello, album number #{Album.count} name is #{name}"
    		end
	end
The method initialize and intro known as instance method. Inside initialize method the self is used as the implicit receiver of the instance method name.
To call the instance method outside the class, 
nee = Album.new(“Amen”)
nee. Initialize	#=> "Hello, album number  1 name is Amen"

Self also help us to know the scope of the objects, to determine whether the method is private or public. 
