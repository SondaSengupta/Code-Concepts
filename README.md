# Code-Concepts
Markdowns of code concepts I want to learn

## Here is a piece of example code:

```javascript
var datasetButtons= ['#fire-station','#police-station','#wifi', '#parks'];

  datasetButtons.forEach(function(dataset){
    $(dataset).click(function(){
      console.log(this);
      //add toggle for showing icons on map
      toggleIcon($(this).attr('id'));
    });
  });
```

##And a picture with a set width:
<img src="http://images.media-allrecipes.com/userphotos/250x250/2836485.jpg" alt="Drawing" width="10px"/>
  
