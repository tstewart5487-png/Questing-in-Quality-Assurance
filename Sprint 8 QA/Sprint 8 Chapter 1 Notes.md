# Chapter 1: Classes and Objects

## Class

- Blueprint or template
- Defines the properties/attributes and behaviors/methods for objects created from it
- Describes how something should look
- Describes its functionality
- Doesn't actually create anything by itself
- Like the recipe for a cake
- Helps avoid duplicate code by providing templates for objects
- Create a class using the `class` keyword followed by the name of your class
  - Capitalize class names to set them apart from other variables
  - Use only digits and Latin characters
  - Don't start with a digit
  - Don't use spaces. If it has more than 1 word use PascalCase. Capitalize each word
- Has to have specific parameters

### Class Variables (attributes)

- Hold parameters that will be shared by all objects
- When they are defined, all the objects created of this class will have those attributes
- Can override a parameter by using `ClassName.variable_name`
  - Changing a variable like this is acceptable for class attributes that must be the same for all objects
  - Changes the attribute for all objects created from the class

### Functions vs. Methods

- A function is a named set of actions; for instance, the `print()` function prints everything specified in the parentheses
- A method is a function that is attached to an object
- Use the `def` keyword to declare a method
  - The name — the same rules apply for function names
  - The `self` argument is required to access object attributes and call the method for objects
    - `self` is a way to tell Python you're referring to a particular object, not just the class in general that the object was created from
  - The method body specifies what the method does

### Example: Cake Class

```python
class Cake:
    # Class variables shared by all Cake objects
    recipe_type = "Basic Cake"
    baking_temperature = 180  # Baking temperature in Celsius
    baking_time = 30          # Baking time in minutes

    def __init__(self, flour, sugar, milk, eggs): # Constructor for initializing new Cake objects
        self.cake_flour = flour  # amount of flour in grams
        self.cake_sugar = sugar  # amount of sugar in grams
        self.cake_milk = milk    # amount of milk in milliliters
        self.cake_eggs = eggs    # number of eggs

        # Methods
    def mix_ingredients(self):
        # Prints a message with the amounts of each ingredient
        print(f"Mixing {self.cake_flour} grams of flour, {self.cake_sugar} grams of sugar, {self.cake_milk} ml of milk, and {self.cake_eggs} eggs.")

    def bake(self):
        # Uses the class variables for temperature and time to print the baking details
        print(f"Baking the cake at {self.baking_temperature}°C for {self.baking_time} minutes.")

    def serve(self):
        # Prints a message indicating the cake is being served
        print("Serving the cake with decoration.")
```

### Breakdown of the Cake Example

- Defined the class `Cake`
  - Blueprint for creating cake objects
  - All objects (cakes) have the variables defined within the class
- Used the method `__init__` (constructor) to initiate the attributes of a class
  - The argument `self` refers to the specific object calling the method
    - It allows us to access the class's attributes and methods in other methods
    - Helps distinguish between instance variables and local variables with the same name
  - `self.cake_flour = flour`
    - `self` is a keyword used to refer to the specific instance of the class that is currently being handled
    - `cake_flour` is the name of the instance variable that will hold the amount of flour needed for this specific cake
      - Adding `cake_` in front of the variable distinguishes it and clarifies that it's a property of the cake object
    - `flour` is the parameter passed to the `__init__` method when creating a new cake object
      - Specifies the amount of flour for the cake being made
- Below the constructor `__init__`, we define our methods: `mix_ingredients()`, `bake()`, `serve()`
- `__init__` is a method built into Python classes
  - Constructor method
  - Used to build an object with different parameters
  - Use the keyword `def` to call the method `__init__(...)`
  - `self` is the required argument to call the method
    - Allows you to refer to an object and assign it unique values
    - Goes first, then after can list all the other attributes that you want to assign to your objects
    - `self` represents the object itself
    - Helps indicate which attributes belong to the specific object
    - You can call this argument whatever you like, but in most cases it's just called `self`. The most important thing is to place it first.
- When creating objects, you will specify these values individually for each object
  - Need to indicate the fields to store these values
  - `self.cake_flour = flour`
    - Object will have a field called `cake_flour` and it will store the `flour` value

## Object

- Instance of a class
- Has specific values for its attributes and can perform actions defined by its methods
- Like the cake made from the recipe
- Shares the same fundamental ingredients listed in the class
- Possible to create multiple objects from a single class
- Can create an object using `object_name = ClassName()`
- Can create multiple objects

## Methods

- Dot operator
- Followed by the method name
- Followed by `()`