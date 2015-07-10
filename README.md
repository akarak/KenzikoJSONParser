# KenzikoJSONParser
A Viz Scripting Language plugin for JSON decoding.

This plugin can be used to load and parse JSON files. 

JSON data is transformed into a multi-level StringMap, with each object property referencable by key.
In the case of JSON arrays, these are transformed into a stringmap where the array index is used as the key (ie "0","1" etc.).

Use the following in your script. 
You will need to reference the plugin as a function plugin, and this will depend on where it is in the Tree. 
This example would work in the scene script.

' Begin example

' Find the container with the plugin on it
dim jsonPlugin = findContainer("KenzikoJSONParser").getFunctionPluginInstance("KenzikoJSONParser").script
jsonPlugin.LoadAndParseJsonFile("path/to/json/file")

' How to access the data:

' Assuming the data looks like {"prop1":"value1","prop2":{"prop3":"value2"}}

' You can get the value for property2 like this:

dim myStringValue = (string)jsonPlugin.GetStringPropertyByPath("prop2/prop3")

' myStringValue will be set to "value2"

' End example

You can also Load JSON direct from URLs using the following:

LoadAndParseFromURL(url as string)

Which will retrieve the JSON from the web and then parse it and return the StringMap. 
