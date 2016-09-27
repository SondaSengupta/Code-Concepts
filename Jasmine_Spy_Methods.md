## What is the difference between and.callThrough(), and.callFake(), or nothing for a Jasmine Test spy?

###What are Jasmine Spies? 
Jasmine has test double functions called spies. A spy can stub any function and track calls to it and track arguments to it as well. A spy only exists in a describe or it block and will be removed after each spec.

###Just calling a Jasmine Spy:  
Just having a spy means that it will track calls to it and can let you know whether it has been called or not. It does not go through the implementation, but actually stops its execution.


```Javascript
foo = {
      setBar: function(value) {
        bar = value;
      }
    };

spyOn(foo, 'setBar');
foo.setBar(123);

it("tracks that the spy was called", function() {
  expect(foo.setBar).toHaveBeenCalled();  //true
}); 

it("stops all execution on a function", function() {
  expect(bar).toBeNull(); //true since it the spy stops execution of the setBar function.
});
```

###Calling Jasmine Spy with and.callThrough()  
By chaining the spy with and.callThrough, the spy will track through the actual implementation of the method in addition to letting you know whether the method and its arguments have been called.

```Javascript
foo = {
      setBar: function(value) {
        bar = value;
      }
  };

spyOn(foo, 'setBar');
foo.setBar(123).and.callThrough();

it("tracks that the spy was called", function() {
  expect(foo.setBar).toHaveBeenCalled();  //true
}); 

it("stops all execution on a function", function() {
  expect(bar).toEqual(123); //true since spy allows it to go through its normal execution
});
```

###Calling Jasmine Spy with and.callFake()
By chaining the spy with and.callThrough, the spy will track and use your fake implementation instead of the actual execution.

```Javascript

it("stops all execution on a function", function () {
    var foo, bar;

    foo = {
        setBar: function (value) {
            return value;
        }
    };

    spyOn(foo, 'setBar').and.callFake(function() {
        return 300;
    });
    foo.setBar(123);

    expect(foo.setBar()).toEqual(123); // 'Expected 300 to Equal 123'. The test will fail b/c the spy hijacks execution and fakes the specified fake implementation instead.
});
```



