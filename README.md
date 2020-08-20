# FAIMS 3.x Scratchpad

Project for experimentation with ideas for the new version of FAIMS.


## JSON Schema

Can we use JSON Schema [JS] as a definition language for an app? 

Translation of existing [Oral History schema](https://github.com/FAIMS/oral-history-doumanis/blob/master/module.xml) into [schema/oralhistory.json](schema/oralhistory.json). 

* I think all of the information that's in the XML file is easily captured in the schema. In some cases I've defined composite types for fields.  I used the description field to contain a label that could be used as a prompt to the user. 

* JS has all the basic types and a few based on string formats but doesn't have a way of defining new types.  What you can do is use a reference to a pre-defined type schema:
```JSON
            "location": {
                "$ref": "#/definitions/street-address"
            },
```
where the actual type is defined in the definitions section - this can be another file or a URL.  The problem is that you can't then add to this - in particular I was using the `description` field to hold a label and you can't add that in here if you use `$ref`.

* My thinking was that each field type might render as a particular form component in the app but on reflection it might be the other way around - each component has an associated schema fragment and one output from an app definition could be a schema to describe the JSON data format that will be used to store and transmit the data. 


