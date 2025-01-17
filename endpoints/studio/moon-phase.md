---
description: Generate an image of the Moon based on the given parameters.
---

# Moon Phase

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/studio/moon-phase" method="post" summary="Generate Moon Phase" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="format" type="string" %}
Image format to be returned. Valid values are 

`png`

 or 

`svg`

. Defaults to 

`png`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="style" type="object" %}
Style object contains the styling parameters for the image generated.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="observer" type="object" %}
Observer object must contain the 

`latitude`

, 

`longitude`

 and 

`date`

 of the observer. 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="view" type="object" %}
View object is used to configure the view of the rendered image. The view object must contain a 

`type`

 object. 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```typescript
{
    "data": {
        "imageUrl": "https://widgets.astronomyapi.com/moon-phase/generated/1234567890.png"
    }
}
```
{% endswagger-response %}
{% endswagger %}

```typescript
{
    "format": "png",
    "style": {
        "moonStyle": "sketch",
        "backgroundStyle": "stars",
        "backgroundColor": "red",
        "headingColor": "white",
        "textColor": "red"
    },
    "observer": {
        "latitude": 6.56774,
        "longitude": 79.88956,
        "date": "2020-11-01"
    },
    "view": {
        "type": "portrait-simple",
        "orientation": "south-up"
    }
}
```

## Format

The API currently supports outputting images in `svg` and `png` formats. These can be used in different use cases, depending on how and where you want them to be displayed.&#x20;

## Style

#### `moonStyle`

Valid values are `default`, `sketch` and `shaded.` Below are sample moons for each value.

![default](../../.gitbook/assets/moon.285d.png)

![shaded](../../.gitbook/assets/moon.285s.png)

![sketch](../../.gitbook/assets/moon.285k.png)

#### `backgroundStyle`

Background style supports the values either `stars` or `solid`. Passing `stars` will render a stars background while `solid` will render the background with a solid color specified by the `backgroundColor` property.

#### `backgroundColor, headingColor and textColor`

These properties could be used to customize the image further. Colors could be defined as hex or as any of the 140 html color names.

## View

#### `type`

The type parameter in the view object should specify which template to be used when rendering the image. Currently two templates are available.

![portrait-simple](../../.gitbook/assets/e86043757e0a337db6d529d42e6c67e9e832b104f75d92bf9e6a09fc4d44cc25.png)

![landscape-simple](../../.gitbook/assets/f2968861e774a453f7826a48bb0c1f41c22693a3b58475cbec0435e97171d8e2.png)

#### `orientation`

Orientation parameter in the view object, determines which orientation to use when rendering the moon. By default it will render north side up, as seen by an observer facing the south side of the sky. This parameter is optional.

Below is an example of the same image with different orientations.

![north-up](../../.gitbook/assets/33574d6b80418fce7f3cb4ba97e09ea0f460f7780b6a3367dda5e58643896230.png)

![south-up](../../.gitbook/assets/0b12c46d2b33d72b4f848cd40d878221e57689ab2880d104d615721912dd5593.png)
