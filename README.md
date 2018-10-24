# EasyJSON
A java based JSON Reader that is designed to be easy and quick to use.

This package is a part of the [ZDoctor's Commons on GitHub](https://github.com/Z-Doctor/ZDoctorsCommons) for those that have need of this certain aspect.

To learn how to use EasyJSON, check out the [wiki](https://github.com/Z-Doctor/EasyJSON/wiki).

# Example Usage
Let's say you have a file named block.json that read this:

```json
{
    "parent": "block/block",
    "elements": [
        {   "from": [ 0, 0, 0 ],
            "to": [ 16, 16, 16 ],
            "faces": {
                "down":  { "texture": "#down", "cullface": "down" },
                "up":    { "texture": "#up", "cullface": "up" },
                "north": { "texture": "#north", "cullface": "north" },
                "south": { "texture": "#south", "cullface": "south" },
                "west":  { "texture": "#west", "cullface": "west" },
                "east":  { "texture": "#east", "cullface": "east" }
            }
        }
    ]
}
```

This is the block.json from Minecraft. An example of how you would read this using EasyJSON would be this:

```java
JSonReader jR = new JSonReader("block.json");
    JSonObject jO = jR.readObject();
    JSonObject elements;
    JSonObject faces;

    jO.getString("parent"); // block/block
    elements = jO.getArray("elements").getObject(0); // [{from=[0, 0, 0], to=[16, 16, 16], faces={east={cullface=east, texture=#east}, south={cullface=south, texture=#south}, north={cullface=north, texture=#north}, west={cullface=west, texture=#west}, up={cullface=up, texture=#up}, down={cullface=down, texture=#down}}}]

    elements.get("from"); // [0, 0, 0]
    elements.get("to"); // [16, 16, 16]
    faces = elements.getObject("faces"); // {east={cullface=east, texture=#east}, south={cullface=south, texture=#south}, north={cullface=north, texture=#north}, west={cullface=west, texture=#west}, up={cullface=up, texture=#up}, down={cullface=down, texture=#down}}

    faces.getObject("east"); // {cullface=east, texture=#east}
    faces.getObject("south"); // {cullface=south, texture=#south}
    faces.getObject("north"); // {cullface=north, texture=#north}
    faces.getObject("west"); // {cullface=west, texture=#west}
```
Of course you would change this depending on what you need. The JSonReader is a HashMap so you can use them however you'd like. Read the wiki for more info.