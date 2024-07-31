# Thriicents Content

This repository acts as a psuedo back-end for the Thriicents website. Updates to the "master" branch will be reflected in real time on the front-end.

## Guides for Updating

The following outlines how to make updates for each of the different content categories.

### Categories

``` jsonc
{
    "Category Name": {
        "color": "blue",            // see "color" below for options
        "src": "..."                // the url of the background image
    },
    ...
}
```

Categories uses "named-objects", meaning, the name of each object is the name of the category.

#### `color`

The `color` property can be one of the following:

- "red"
- "orange"
- "yellow"
- "green"
- "blue"
- "purple"
- "pink"

#### `src`

The `src` property is the exact URL of the background image for the category. To use the thumbnail of a YouTube video as the background, use the YouTube thumbnail URL format:

``` sh
# replace <video-id> with the id of the desired video

https://img.youtube.com/vi/<video-id>/0.jpg
```

### Videos

``` jsonc
{
    "Video Name": {
        "id": "...",                // the YouTube video ID
        "duration": "1:20",         // the duation timestamp
        "description": "...",       // the description to show below the video
        "uploaded": "Jan 1, 1990",  // the updload date for the video
        "category": "MyThriicents"  // the category for the video
    }
}
```

Videos uses "named-objects", meaning, the name of each object is the title of the video.

#### `id`

The YouTube video ID for the video. You can get the YouTube video ID from the URL of the video:

``` sh
https://www.youtube.com/watch?v=2YZy20-jjeI
#                               ^^^^^^^^^^^
```

The ID is the part of the URL directly following the `v=` URL variable.

If the URL contains other variables, be sure not to include them:

``` sh
https://www.youtube.com/watch?v=gjYbD1Gk96Y&list=PL0v3oDkZwh-9aVbFAQBreq6r2K3L514RN
#                               ^^^^^^^^^^^xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
#                               only this  nothing after (or including) the "&"
```

#### `duration`

The duration is simply the timestamp you wish to show at the bottom of the video thumbnail. You can get this data from the YouTube video. Simply write the timestamp as `MM:SS`.

#### `description`

The description is any text you want to include under the video. The text supports some Markdown syntax including:

``` md
[links](https://link.path)

*italic text*

**bold text**

- unordered
- lists

1. ordered
2. lists
```

Headings are not currently supported and should not be used as they would break the symantic structure of the page.

> [!NOTE]
> All text, including Markdown text, must be JSON encoded before adding. You can use a tool like [JSON formatter](https://jsonformatter.org/json-stringify-online) to automatically encode your text.

#### `uploaded`

The `uploaded` property should be the date the video was uploaded. The value can be any valid date-string as it is parsed by the website and reformatted. Valid date strings include:

- `"Jul 7, 2024"`
- `"2024-07-30"`
- `"July 30, 2024"`
- `"07/30/2024"`
- `"30 July 2024"`

#### `category`

For `category`, be sure to include the *exact name* of an existing Category. Invalid values here could cause issues. The selected category will determine where the video is housed on the website.

### Word

``` jsonc
{
    "text": "...",                  // the content of the quote
    "source": "...",                // the person to cite
    "videoId": "..."                // the YouTube video ID for the related video
}
```

Words are stored in an array meaning that objects have no titles. Simply wrap the object in a `{}` without any prefix or key.

#### `text`

The text is the main body of the quote. No fancy formatting of Markdown is permitted here, just plain text.

#### `source`

The name of the person you are citing.

#### `videoId` *(Optional)*

This should just be the video ID for the video you want to link to this quote. Words with a `videoId` will show a link inside of them to the video in question. Videos that are linked to a quote will show that quote under the video. Multiple quotes can be linked to a single video.

