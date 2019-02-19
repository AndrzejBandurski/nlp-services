[issue-template]: ../../../issues/new?template=BUG_REPORT.md
[feature-template]: ../../../issues/new?template=FEATURE_REQUEST.md

![singnetlogo](../assets/singnet-logo.jpg?raw=true 'SingularityNET')

# Named Entity Recognition Service

It is part of our [NLP Services](https://github.com/singnet/nlp-services).

### Welcome

The service receives as sentences and identify ORGANIZATION, PLACE and PERSON entities.

### What’s the point?

The service process input sentences and returns all the identified entities. 

### How does it work?

The user must provide the following inputs:

 - `value`: text sentence.
 

The output format is:
 - `value`: identified entities it's positions in the input sentence in base64.
 
You can use this service from [SingularityNET DApp](http://beta.singularitynet.io/).

You can also call the service from SingularityNET CLI (`snet`).

Assuming that you have an open channel (`id: 0`) to this service:

#### Input data example:

For this example use this sentence as input data:

Our concept of operations is to flow in our military assets with a priority to build up southern Texas, and then Arizona, and then California," Donald Trump said Monday, adding that the soldiers normally assigned weapons will be carrying them at the border. "We'll reinforce along priority points of entry, and while this happens, Trump Hotels is falling down in stock market.

Encode in base64 utf-8 text and the result will be like this:
```
T3VyIGNvbmNlcHQgb2Ygb3BlcmF0aW9ucyBpcyB0byBmbG93IGluIG91ciBtaWxpdGFyeSBhc3NldHMgd2l0aCBhIHByaW9yaXR5IHRvIGJ1aWxkIHVwIHNvdXRoZXJuIFRleGFzLCBhbmQgdGhlbiBBcml6b25hLCBhbmQgdGhlbiBDYWxpZm9ybmlhLCIgRG9uYWxkIFRydW1wIHNhaWQgTW9uZGF5LCBhZGRpbmcgdGhhdCB0aGUgc29sZGllcnMgbm9ybWFsbHkgYXNzaWduZWQgd2VhcG9ucyB3aWxsIGJlIGNhcnJ5aW5nIHRoZW0gYXQgdGhlIGJvcmRlci4gIldlJ2xsIHJlaW5mb3JjZSBhbG9uZyBwcmlvcml0eSBwb2ludHMgb2YgZW50cnksIGFuZCB3aGlsZSB0aGlzIGhhcHBlbnMsIFRydW1wIEhvdGVscyBpcyBmYWxsaW5nIGRvd24gaW4gc3RvY2sgbWFya2V0Lg==
```

#### Service call example:
```

$ snet client call 0 0.00000001 54.203.198.53:7012 Recognize '{"value": "T3VyIGNvbmNlcHQgb2Ygb3BlcmF0aW9ucyBpcyB0byBmbG93IGluIG91ciBtaWxpdGFyeSBhc3NldHMgd2l0aCBhIHByaW9yaXR5IHRvIGJ1aWxkIHVwIHNvdXRoZXJuIFRleGFzLCBhbmQgdGhlbiBBcml6b25hLCBhbmQgdGhlbiBDYWxpZm9ybmlhLCIgRG9uYWxkIFRydW1wIHNhaWQgTW9uZGF5LCBhZGRpbmcgdGhhdCB0aGUgc29sZGllcnMgbm9ybWFsbHkgYXNzaWduZWQgd2VhcG9ucyB3aWxsIGJlIGNhcnJ5aW5nIHRoZW0gYXQgdGhlIGJvcmRlci4gIldlJ2xsIHJlaW5mb3JjZSBhbG9uZyBwcmlvcml0eSBwb2ludHMgb2YgZW50cnksIGFuZCB3aGlsZSB0aGlzIGhhcHBlbnMsIFRydW1wIEhvdGVscyBpcyBmYWxsaW5nIGRvd24gaW4gc3RvY2sgbWFya2V0Lg=="}'
```

#### Output example:

The result will be a base64 text like this:

```
WygnVGV4YXMnLCAnTE9DQVRJT04nLCAnU3RhcnQgc3BhbjonLCA5NywgJ0VuZCBzcGFuOicsIDEwMiksICgnQXJpem9uYScsICdMT0NBVElPTicsICdTdGFydCBzcGFuOicsIDExMywgJ0VuZCBzcGFuOicsIDEyMCksICgnQ2FsaWZvcm5pYScsICdMT0NBVElPTicsICdTdGFydCBzcGFuOicsIDEzMSwgJ0VuZCBzcGFuOicsIDE0MSksICgnRG9uYWxkIFRydW1wJywgJ1BFUlNPTicsICdTdGFydCBzcGFuOicsIDE0NCwgJ0VuZCBzcGFuOicsIDE1NiksICgnVHJ1bXAgSG90ZWxzJywgJ09SR0FOSVpBVElPTicsICdTdGFydCBzcGFuOicsIDMzMSwgJ0VuZCBzcGFuOicsIDM0Myld
```

After you decode the base64 result the output will be like this:

```
$ [('Texas', 'LOCATION', 'Start span:', 97, 'End span:', 102), ('Arizona', 'LOCATION', 'Start span:', 113, 'End span:', 120), ('California', 'LOCATION', 'Start span:', 131, 'End span:', 141), ('Donald Trump', 'PERSON', 'Start span:', 144, 'End span:', 156), ('Trump Hotels', 'ORGANIZATION', 'Start span:', 331, 'End span:', 343)]

```

For more details about how to call SingularityNET services, please read our [How to publish a service](https://github.com/singnet/wiki/tree/master/tutorials/howToPublishService) tutorial.