An introduction to Programming in Ruby using irb


##Getting started



*irb is the Interactive RuBy shell.  You can type Ruby code and it will be evaluated immediately. You can try some code that will seem familiar:


>>1 + 1


*try a few different calculations


*now try this one


>>"c" + "ode"


*why was this different? in Ruby everything is an object and each object has behaviors it knows how to do.  Numbers know how to add.  However "c" is not a number, so it behaves differently even when it gets the same message (+).  Programmers call "c" or "ode" a "string." A string is series of letters that could be a word or a sentence.  In Ruby the string behavior triggered by the (+) message is concatenation.


*Operators like + - * / are special since we want to use them like we did in grade school.


*Most messages (which are also called methods) are called by adding the message name after a .


>>"code".upcase
"code".reverse


*Another thing to notice about Ruby is that everything evaluates to something


>>4
4 + 4
(4+4).zero?


*Notice how parentheses can change behavior. Parentheses cause the stuff inside to be evaluated first, otherwise the '.' has the highest precedence.  Remember "Please Excuse My Dear Aunt Sally?" The same rules apply, with . at the beginning.


>>"c" + "ode".upcase
("c" + "ode").upcase##Variables



Variables can hold a value


>> a = 4
>> a
>> b = 2
>> a + b


In Ruby (unlike languages like C or Java), variables can be of any type and can change type


>> a = "cat"


But types do matter.  For example, this is an error:


>> "cat" + 4
TypeError: can't convert Fixnum into String
from (irb):4:in `+'
from (irb):4


But this works:


>> "cat" + 4.to_s


Variables are useful when you start writing reusable code.


##Defining Classes and Methods



We define a new type of object by writing something called a "class." The behavior of the object is defined in blocks of code we call "methods."


As an example we'll create a Calculator kind of object that knows how to describe itself in text.  At first, that is all it will know how to do.


class Calculator    
  def describe
   "I am a really neat calculator!"
  end   
end


save this in a file in your text editor called "calculator.rb" then start irb in the same directory


>> load "calculator.rb"
>> c = Calculator.new
>> c.describe


next we'll add a method that performs a calculation


def add(a, b)
  a + b
end


then restart irb and try it:


>> load "calculator.rb"
>> c = Calculator.new
>> c.add(1,2)
>> c.add(56,45)


The same code can be reused with different inputs


Now, why might we have a calculator object when Ruby can already do built in calculations.  Suppose we wanted to keep track of when we did different calculations, how many each calculator had done.  We might have two calculators and have each store the number of calculations it had performed.  Each object can actually keep its own data with it, even though the code that defines each object is identical.  We call each object an "instance" of the class and so we call this object data and "instance variable"


class Calculator
  def initialize
    @num_calculations = 0
  end

  def how_many
    @num_calculations
  end

  def describe
    "I am a really neat calculator!"
  end

  def add(a, b)
    @num_calculations = @num_calculations + 1
    a + b
  end

end


##Arrays



>> my_fruits = ["kiwi", "strawberry", "plum"]
=> ["kiwi", "strawberry", "plum"]

>> my_fruits = my_fruits + ["lychee"]
=> ["kiwi", "strawberry", "plum", "lychee"]
>> my_fruits = my_fruits - ["lychee"]
=> ["kiwi", "strawberry", "plum"]


##Hashes



>> states = {"CA" => "California", "DE" => "Delaware"}
=> {"DE"=>"Delaware", "CA"=>"California"}

>> states["DE"]
=> "Delaware"


##Repeating yourself



>> puts fruits[0]
kiwi
=> nil
>> puts fruits[1]
strawberry
=> nil
>> puts fruits[2]
plum
=> nil


Easier to write this:


>> fruits.each do |f|
* puts f
>> end
kiwi
strawberry
plum


(Omit asterisk before 'puts f' and code below, it denotes start of new line and not part of the code)


##Conditions



if true


puts "you will see this"


end


if false


puts "you won't see this"


end


puts "you will see this" if true


###Truth



Everything is true except for


*false


*nilTherefore


*0 is true


*"" is true###Equality



Testing for equality is different from setting equality:


a = 4
   puts "four" if a == 4


Another example:


>> fruits.each do |f|
*   puts f if f == "plum"
>> end
plum