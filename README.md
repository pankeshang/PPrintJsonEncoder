# PPrintJsonEncoder
a JSON encoder that allow use set a "depth" attribute in order to fine tune the output JSON string.

This encoder is compatible with the default python json module.

The ``depth`` attribute only works when the ``indent`` attribute is set to a non-zero value.

##Example##

```
>>> import json
>>> from pp_json_encoder import PPJSONEncoder
>>> data_structure = {
...         'layer1': {
...             'layer2': {
...                 'layer3_1': [{"x":1,"y":7}, {"x": 0, "y": 4}, {"x": 5, "y": 3}, {"x":6,"y":9}],
...                 'layer3_2': 'string'
...             }
...         }
...     }
>>> print json.dumps(data_structure, indent=2, cls=PPJSONEncoder, depth=2)
{
  "layer1": {
    "layer2": {"layer3_2": "string", "layer3_1": [{"y": 7, "x": 1}, {"y": 4, "x": 0}, {"y": 3, "x": 5}, {"y": 9, "x": 6}]}
  }
}
>>> print json.dumps(data_structure, indent=2, cls=PPJSONEncoder, depth=3)
{
  "layer1": {
    "layer2": {
      "layer3_2": "string", 
      "layer3_1": [{"y": 7, "x": 1}, {"y": 4, "x": 0}, {"y": 3, "x": 5}, {"y": 9, "x": 6}]
    }
  }
}
>>> print json.dumps(data_structure, indent=2, cls=PPJSONEncoder, depth=4)
{
  "layer1": {
    "layer2": {
      "layer3_2": "string", 
      "layer3_1": [
        {"y": 7, "x": 1}, 
        {"y": 4, "x": 0}, 
        {"y": 3, "x": 5}, 
        {"y": 9, "x": 6}
      ]
    }
  }
}
>>> print json.dumps(data_structure, indent=2, cls=PPJSONEncoder, depth=5)
{
  "layer1": {
    "layer2": {
      "layer3_2": "string", 
      "layer3_1": [
        {
          "y": 7, 
          "x": 1
        }, 
        {
          "y": 4, 
          "x": 0
        }, 
        {
          "y": 3, 
          "x": 5
        }, 
        {
          "y": 9, 
          "x": 6
        }
      ]
    }
  }
}
```