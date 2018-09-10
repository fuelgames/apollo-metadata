
# Apollo-Metadata

A metadata specification for non-fungible assets which provides for hierarchies of asset classes. 

Asset classes recognise that while each asset is unique, assets often share 'class' properties which are meaningful to users and should be displayed appropriately by inventories and marketplaces, and uses this understanding to reduce information duplication in asset properties. 

It will aim to maintain compatibility with previous standards through translaters rather than by implementing standards side-by-side. 

## Specification

Assets should store the following metadata:

```
{
    "name": "optional",
    "description": "optional",
    "class_url": "optional_url",
    "image_url": "optional_url",
    "external_url": "optional_url",
    "properties": {
        "power": {
            "value": 0,
            "type": "range_number",
            "max": 100,
        }
    }
}
```

By following the optional ```class_url``` parameter, the class properties of the asset are also displayed:

```
{
    "name": "optional",
    "description": "optional",
    "parent_url": "optional_url",
    image_url: "otional_url",
    "properties": {
        "colour": {
            "value": "red"
        }
    }
}
```

The ```parent_url``` field allows for classes to have parents with inherited properties. Crawlers may want to set a max depth and implement anti-recursion logic on this field. 

## Examples

A simple example of a mock class hierarchy for Etherbot part ```#1000```, a shadow lambo. 

### Asset Metadata

```
{
    "class_url": "https://etherbots.io/class/shadow-lambo
    "properties": {
        "experience": {
            "value": 10000,
            "type": number
        }
    }
}
```

### Asset Class

```
{
    "name": "Shadow Lambo",
    "image_url": "https://etherbots.io/image/lambo/shadow
    "parent_url": "https://etherbots.io/class/lambo"
    "properties": {
        "rarity": {
            "value": "Shadow"
        }
    }
}
```

```
{
    "name": "Lambo",
    "properties": {
        "type": {
            "value": "melee"
        }
        "element": {
            "value": "steel"
        }
    }
}
```

