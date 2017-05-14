# Dynamic Content Ads Standard #
## Schema Specification Version 1.0 ##
### Released September 2016 ##

## About the IAB Technology Lab ##

The IAB Technology Laboratory is a nonprofit research and development consortium charged with producing and helping companies implement global industry technical standards and solutions. The goal of the Tech Lab is to reduce friction associated with the digital advertising and marketing supply chain while contributing to the safe growth of an industry.
The IAB Tech Lab spearheads the development of technical standards, creates and maintains a code library to assist in rapid, cost-effective implementation of IAB standards, and establishes a test platform for companies to evaluate the compatibility of their technology solutions with IAB standards, which for 18 years have been the foundation for interoperability and profitable growth in the digital advertising supply chain.

The Dynamic Content Ad Standards Working Group is a working group within the IAB Technology Lab. Further details about the IAB Technology Lab can be found at: [www.iabtechlab.com](https://www.iabtechlab.com)

For more detials on the working group, please visit [https://iabtechlab.com/working-groups/dynamic-content-ad-standards/](https://iabtechlab.com/working-groups/dynamic-content-ad-standards/)

Shailley Singh  
Senior Director of Product and R&D  
IAB Technology Lab  
[shailley@iabtechlab.com](mailto:shailley@iabtechlab.com)


## License/Intellectual Property Notice ##
Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
 1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
 2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
 3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## Schema ##
### Executive Summary ###
Programmatic has made dynamic media a reality, with individual ad placements chosen based on an avalanche of data. While to date, data has been mostly used to inform the media components of the ad, ad tech’s embrace of the creative half of the ad equation is exploding, reflecting marketer’s desire to bring the best technology forward to optimize the right message part of the holy trinity of right message, right person, right place & time with “dynamic” creative.

The need is coming from agencies and brands under two major requirements:

* Desire to optimize content advertising on social media and other content distribution platforms. In this environment, it quickly becomes overwhelming for an agency to create the myriad versions of the same content necessary to cover multiple platforms.  Often, this is as simple as a headline, key visual, disclosure, brand ID, and a call to action—yet varying specs can make versioning onerous to say the least.
* The other need has been that marketers are recognizing the need for “in-the moment” messaging where getting the right message at the right time to the user could significantly influence purchase decisions.

Media targeting has gotten much, much better, but creative has barely evolved. A leap forward was made with version one of dynamic creative optimization, but last generation DCO was limited by the need to create multiple finished ads (that were dynamically served based on decision engines, not dynamically created).

Recently, however, the groundwork has been laid for a massive leap forward in truly dynamic advertising as marketers’ ability to create more distinct commercial options and creative assets catches up with ad tech’s ability to target, render, and serve them.

Dynamic Content Ad Standard aims to address this opportunity driving the demand for Dynamic Ad Component standards.
Of perhaps equal importance to the ad ops and ad tech communities, robust standards will create a foundation for development and implementation that will lead to faster, easier adoption and the freeing up of resources for innovation.

### Introduction ###
Dynamic Ad content standards is a structured system of meta-data for creative components and asset variations of the creative components that may be used in an advertisement. It also defines a standard delivery structure that is extensible for custom asset types.
The specification as defined is agnostic of the technology used. But is delivered with a JSON schema.
The standard is generic enough that it can be applied to any type of ad format. But specific use case is for dynamic creative optimization and serving real time personalized creative based on available user, context and other advertising targeting data.
The standard defines all the creative assets that can be used in an ad creative as well as creative groupings.
### Version 1.0 Scope ###
The scope for Version 1.0 of Dynamic Content Ads standards will be limited to Ad units that do not have complex rich media components like expansion, multiple interactive or user engagement elements and do not require complex layouts.
The following type of ad units are in scope:
* Static or single layer creative  Ad units 
* Ad units with with images and texts
* Ad Units with simple animation using core HTML5 technologies like CSS or JS or SVG
* Ad Units with single Video engagement that plays in banner
* Ad units with single “click out” user engagement
* Dynamic Video- delivered via vpaid or other creative in VAST

The following type of Ad units are out of scope:
* Rich Media units with expansion and multiple layers of creative components
* Rich interactive units with multiple user engagement creative components

### Audience and Usage ###
The standards is designed to guide the following audience to communicate the creative components and their asset variations in a standardized format.
* Creative Developers can define the creative components and assets to be used in a structured manner as well as assets groupings based on creative design
* Creative Platforms can integrate the schema in their platforms so they can output the schema to be delivered to ad servers and design their ad tags in a way that can invoke and use the schema to determine what creative asset to use
* Ad Content Management Systems providers can integrate the schema definition to store all the assets with unique identifiers and naming for serving and reporting purpose
* Ad serving systems - Ad servers, DSPs, Ad Tech providers can use the schema to make real time decisions on which assets to use for a particular impression and serve personalized and relevant ad creative. In addition they can track the assets for performance and optimization of advertiser objectives and ad effectiveness
* Media agencies and Operations can use the schema to track different creative assets and for reporting on the performance

## Specification ##
Below is the specification detail for Version 1.0.

| Parameter                    | Parameter Attributes | Req. | Description                                                                                                                                                                                        |
|------------------------------|----------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ad                           |                      | Y    | Captures top level Ad or campaign information                                                                                                                                                      |
| (occurs:1)                   |                      |      |                                                                                                                                                                                                    |
|                              | id                   | Y    | Unique identifier - e.g. ad server or buyer system identifier                                                                                                                                      |
|                              | name                 | Y    | Human friendly name for reporting                                                                                                                                                                  |
|                              | advertiser           | Y    |                                                                                                                                                                                                    |
| ad/version                   | Version Number                      | Y    | This represents the version number for this ad if it has undergone changes. Each new version must be usable by itself and not require another version to determine any detail                                                                                                                              |
| ad/adUnits                   |                      | Y    | All ad units that are part of the top level ad must be defined here                                                                                                                              |
| (occurs > 1)                 |                      |      |                                                                                                                                                                                                    |
|                              | id                   | Y    | Sequential number starting at 1/ buyer or ad tech vendor system identifier                                                                                                                         |
|                              | name                 | Y    | Human friendly name for reporting                                                                                                                                                                  |
|                              | size                 | N    | Use IAB ad sizes                                                                                                                                                                                   |
|                              |                      |      |                                                                                                                                                                                                    |
| ad/assetGroups               |                      | N    | Asset group identifies creative assets that need to be together in a creative execution for targeting or other purpose. This parameter holds the list of valid groups that can be used for this ad |
| (occurs >1)                  |                      |      |                                                                                                                                                                                                    |
|                              | id                   | Y    | The Id can be sequential id starting with 1 or an id assigned by the system that creates this document                                                                                                                                 |
|                              | name                 | Y    | Name of the group that describes the grouping reason and/or assets that are part of the group                                                                                                      |
|                              |                      |      |                                                                                                                                                                                                    |
| ad/creativeComponents/       |                      | Y    | Creative component is different components of the ad creative used to build the ad - e.g. background image, log, text, CTA button etc.                                                             |
| (occurs > 1)                 |                      |      |                                                                                                                                                                                                    |
|                              | id                   | Y    | Sequential number starting at 1                                                                                                                                                                    |
|                              | name                 | Y    | Human friendly name for reporting                                                                                                                                                                  |
|                              | assetType            | Y    | Asset type is type of creative asset i.e. image, text etc.                                                                                                                                         |
|                              |                      |      | The enumeration list is:                                                                                                                                                                           |
|                              |                      |      | html                                                                                                                                                                                               |
|                              |                      |      | javascript                                                                                                                                                                                         |
|                              |                      |      | css                                                                                                                                                                                                |
|                              |                      |      | image (png, jpeg)                                                                                                                                                                                  |
|                              |                      |      | animatedImage (gif) (can this be image)                                                                                                                                                            |
|                              |                      |      | media - for audio and video                                                                                                                                                                        |
|                              |                      |      | svgImage                                                                                                                                                                                           |
|                              |                      |      | webGl                                                                                                                                                                                              |
|                              |                      |      | dataFeed                                                                                                                                                                                           |
|                              |                      |      | assetFeed                                                                                                                                                                                          |
|                              |                      |      | Text                                                                                                                                                                                               |
|                              |                      |      | Fonts                                                                                                                                                                                              |
|                              |                      |      | URI                                                                                                                                                                                                |
|                              |                      |      | custom                                                                                                                                                                                             |
|                              |                      |      | For custom define custom with key value pair the name of asset type.                                                                                              |
|                              | componentDescription        | N    | Defines what type is the component e.g. logo, background image, display url, price etc. There is no industry standard nomenclature at this time but some suggested descriptions to use are:  |
|                              |                      |      | title: a title for the ad
      |
|                              |                      |      | sponsored: "Sponsored By" message where response should contain the brand name of the sponsor.
      |
|                              |                      |      | desc: Descriptive text associated with the product or service being advertised. Longer length of text in response may be truncated or eclipsed by the exchange.
      |
|                              |                      |      | ratings: Rating of the product being offered to the user. For example an app’s rating in an app store from 0-5.
      |
|                              |                      |      | likes: Number of social ratings or “likes” of the product being offered to the user.
      |
|                              |                      |      | downloads: Number downloads/installs of this product
      |
|                              |                      |      | price: Price for product/app/in-app purchase. Value should include currency symbol in localized format.
      |
|                              |                      |      | saleprice: Sale price that can be used together with price to indicate a discounted price compared to a regular price. Value should include currency symbol in localized format.
      |
|                              |                      |      | phone: Phone number
      |
|                              |                      |      | address: Address
      |
|                              |                      |      | desc2: Additional descriptive text associated with the product or service being advertised
      |
|                              |                      |      | displayurl: Display URL for the ad. To be used when sponsoring entity doesn’t own the content. IE sponsored by BRAND on SITE (where SITE is transmitted in this field).
      |
|                              |                      |      | ctatext: CTA description - descriptive text describing a ‘call to action' button for the destination URL.
      |
|                              |                      |      | custom: Additional ad components required or offered by the publisher.
      |
|                              |                      |      | productTitle: Name of product being advertised
      |
|                              |                      |      | productDescription: Description of product being advertised
      |
|                              |                      |      | offerText: Text for the special offer being advertised
      |
|                              |                      |      | productImage:Image of the product being advertised
      |
|                              |                      |      | backgroundImage: Image that covers the full background of the advertisement
      |
|                              |                      |      | logo: Advertiser logo image
      |
|                              |                      |      | logoURL: Image source If the logo image is being provided through advertiser url
      |
|                              |                      |      | offerTextURL: Creative asset most likely image source If the offer text is provided through URL- this can help if offer needs to change dynamically
      |
|                              |                      |      | offerImageURL: An offer may be provided as an image via proving a url for the image source
      |
|                              |                      |      | ctaURL: If the Call to action is dynamic and is being provided via URL
      |
|                              |                      |      | backgroundURL: If the background image or content  is provided via URL
      |
|                              | adUnit               | Y    | Array of ad units that this component can be used in                                                                                                                                               |
|                              |                      |      | <id1, id2, id3>                                                                                                                                                                                    |
|                              |                      |      | Must validate with the list of ad units                                                                                                                                                            |
|                              |                      |      |                                                                                                                                                                                                    |
| ad/creativeComponents/assets |                      | Y    | Asset variants for each creative component                                                                                                                                                         |
| (occurs > 1)                 |                      |      |                                                                                                                                                                                                    |
|                              | id                   | Y    |                                                                                                                                                                                                    |
|                              | name                 | Y    |                                                                                                                                                                                                    |
|                              | source               | Y    | Source address/definition from where to retrieve the creative asset. This includes the file name                                                                                                   |
|                              | sourceType           | Y    | Type of source                                                                                                                                                                                     |
|                              |                      |      | uri                                                                                                                                                                                                |
|                              |                      |      | relative                                                                                                                                                                                           |
|                              |                      |      | embedded                                                                                                                                                                                           |
|                              | fallback             | Y    | This is default value if a decision on what creative asset to use cannot be made.                                                                                                                  |
|                              |                      |      | Values are                                                                                                                                                                                         |
|                              |                      |      | 1 if this is the fall back                                                                                                                                                                         |
|                              |                      |      | 0 if this is not the fallback                                                                                                                                                                      |
|                              | target               | N    | This will tag a particular asset to a target so the system knows where this asset can be used. E..g values are audience, weather, location                                                         |
|                              | assetGroupIds        | N    | Array of ids for an asset. This is to indicate assets that need to be part of the same creative execution or need to be together.                                                                  |
|                              | attributes           | N    | These are attributes specific to asset types. Key value pair to be used to define the attributes. These will vary for each asset type. Attributes must be used as key value pair as follows        |
|                              |                      |      |                                                                                                                                                                                                    |
|                              |                      |      | attributes": {                                                                                                                                                                                     |
|                              |                      |      | "<attribute1>": "<value>",                                                                                                                                                                         |
|                              |                      |      | "<attribute2>": "<value>                                                                                                                                                                           |
|                              |                      |      |                                         }                                                                                                                                                          |
|                              |                      |      |                                                                                                                                                                                                    |
|                              |                      |      | E.g. for media asset type of video                                                                                                                                                                 |
|                              |                      |      | attributes": {                                                                                                                                                                                     |
|                              |                      |      | "weight": "29.6MB",                                                                                                                                                                                |
|                              |                      |      | "aspect ratio": "16:9",                                                                                                                                                                            |
|                              |                      |      | "codec": "H264",                                                                                                                                                                                   |
|                              |                      |      | "resolution": "low"                                                                                                                                                                                |
|                              |                      |      |                               }                                                                                                                                                                    |
|                              |                      |      | List of suggested attributes is provided but other values as needed may be used                                                                                                                    |

### Suggested Asset Attributes ###
These are suggested attributes to define the assets properly. Users may use their own values or custom values based upon use cases.

| Asset Type      | Attribute    | Data Type                        | Description                                                | Example Value                     |
|-----------------|--------------|----------------------------------|------------------------------------------------------------|-----------------------------------|
| HTML            | weight       | Integer                          | K weight of HTML in kb                                     | 110                               |
|                 | filename     | string                           | Name of the html file                                      | index.html                        |
| JS (Javascript) | weight       | Integer                          | K weight of JS file in kb                                  | 5                                 |
|                 | filename     | string                           | Name of the html file                                      | animate.js                        |
| CSS             | weight       | Integer                          | K weight of CSS Ęfile in kb                                | 5                                 |
|                 | filename     | string                           | Name of the css file                                       |                                   |
| IMG (Image )    | weight       | integer                          | K weight of image file in Kb                               | 25                                |
|                 | transparency | boolean                          | Supports transparency                                      | 0 or 1                            |
|                 | mime         | string                           | Mime type value                                            | image/jpeg                        |
|                 | watermark    | string                           | Brand ownership indication                                 | Brand name                        |
|                 | filename     | string                           | Name of the image file                                     |                                   |
| GIF             | weight       | integer                          | K weight of image file in Kb                               | 25                                |
|                 | framerate    | integer                          | Framerate per second                                       | 12                                |
|                 | mime         | string                           | Mime type value                                            | image/gif                         |
|                 | watermark    | string                           | Brand ownership indication                                 | Brand name                        |
|                 | filename     | string                           | Name of the GIF file                                       |                                   |
| Media           | weight       | integer                          | K weight of image file in Kb                               | 25                                |
|                 | Aspect ratio | string                           | Aspect ratio of the video                                  | 16:09                             |
|                 | mime         | string                           | Mime type value                                            | audio/x-aiff or video/mpeg        |
|                 | watermark    | string                           | Brand ownership indication                                 | Brand name                        |
|                 | codec        | string                           | Codec used                                                 | h.264                             |
|                 | duration     | integer                          | Time in seconds for playing the media                      | 6, 15, 30                         |
|                 | resolution   | string                           | Media quality resolution                                   | High-1080 p o higher              |
|                 |              |                                  |                                                            | Medium- 720 p                     |
|                 |              |                                  |                                                            | Low- SD                           |
|                 |              |                                  |                                                            | Raw video for raw mezzanine files |
|                 | filename     | string                           | Name of the media file                                     |                                   |
| SVG             | weight       | integer                          | K weight of image file in Kb                               | 25                                |
|                 | watermark    | string                           | Brand ownership indication                                 | Brand name                        |
|                 | filename     | string                           | Name of the SVG file                                       |                                   |
| WebGL           | weight       | integer                          | K weight of image file in Kb                               | 25                                |
|                 | watermark    | string                           | Brand ownership indication                                 | Brand name                        |
|                 | library      | string                           | URI of the library                                         | pixi.js                           |
|                 | filename     | string                           | Name of the WebGL file                                     |                                   |
| Data Feed       | format       | string                           | Format of the web feed. E,g, from facebook, twitter etc    | JSON                              |
|                 |              |                                  |                                                            | RSS                               |
|                 |              |                                  |                                                            | XML                               |
|                 |              |                                  |                                                            | Atom                              |
|                 |              |                                  |                                                            | CSV                               |
|                 | key          | string                           | Access key or token                                        |                                   |
|                 | user         | string                           | User account for access                                    |                                   |
| Asset Feed      | format       | string                           | Format of the web feed. E,g, from facebook, twitter etc    | JSON                              |
|                 |              |                                  |                                                            | RSS                               |
|                 |              |                                  |                                                            | XML                               |
|                 |              |                                  |                                                            | Atom                              |
|                 |              |                                  |                                                            | CSV                               |
|                 | key          | string                           | Access key or token                                        |                                   |
|                 | user         | string                           | User account for access                                    |                                   |
|                 | vendor       | string                           | Feed provider vendor name or url                           |                                   |
|                 | fields       | array                            | Fields from the freed to be used for creative              | id:text                           |
| Text            | language     | String (3 letter ISO 693-2 code) | Text language. Codes available here                        | Eng for English                   |
|                 |              |                                  | https://www.loc.gov/standards/iso639-2/php/code_list.php ) |                                   |
|                 | style        | string                           | CSS style statement for text                               | CSS pairs                         |
| Font            | weight       | integer                          | K weight of the font file in kb                            | 30                                |
|                 | format       | string                           | Font format and other detail required for rendering        | True type                         |
|                 |              |                                  |                                                            | Open type                         |
|                 | vendor       | string                           | Font provider/ source                                      | Monotype                          |
|                 |              |                                  |                                                            | Google                            |
