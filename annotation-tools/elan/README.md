# README

# Conversion between W3C web annotation & ELAN (provisional)

The following example shows what happens when ELAN imports the example, "unified" W3C annotation file and exports it again. In this first conversion attempt, an **AnnotationCollection** has been considered equivalent to a **Tier** in tier-based data models (like ELAN's).   

## Example W3C annotation

This is a simple text annotation targeting a media fragment and a simple AnnotationCollection with 1 item

```
[
    {
        "@context": "http://www.w3.org/ns/anno.jsonld",
        "id": "http://example.com/annotations/collection1",
        "type": "AnnotationCollection",
        "label": "Tier 1",
        "creator": {
            "type": "Person",
            "nickname": "John Bell",
            "email_sha1": "2bb2a925eb5ac9fd97fc4c041fabc050f194392d"
        },
        "total": 1,
        "first": {
            "id": "Tier 1 Set 1",
            "type": "AnnotationPage",
            "startIndex": 0,
            "items": [
                {
                    "id": "http://example.com/annotations/195",
                    "type": "Annotation"
                }
            ]
        }
    },
    {
        "context": "http://www.w3.org/ns/anno.jsonld",
        "id": "http://example.com/annotations/195",
        "created": "2018-07-10T17:30:04.639Z",
        "generated": "2018-07-14T15:13:28Z",
        "motivation": "highlighting",
        "type": "Annotation",
        "rights": "https://creativecommons.org/publicdomain/zero/1.0/",
        "creator": {
            "type": "Person",
            "nickname": "John Bell",
            "email_sha1": "2bb2a925eb5ac9fd97fc4c041fabc050f194392d"
        },
        "generator": {
            "id": "http://example.org/waldorf",
            "type": "Software",
            "name": "Waldorf.js v1.0",
            "homepage": "http://github.com/novomancy/Waldorf"
        },
        "body": {
            "id": "http://example.com/vocabulary/1/example",
            "value": "Example",
            "language": "en",
            "purpose": "tagging",
            "format": "text/plain",
            "type": "TextualBody"
        },
        "target": {
            "id": "http://mediaecology.dartmouth.edu/other/KTLAEulaLove.mp4",
            "type": "Video",
            "selector": {
                "conformsTo": "http://www.w3.org/TR/media-frags/",
                "type": "FragmentSelector",
                "value": "t=2.019,13.007"
            }
        }
    }    
]
```

## After import in ELAN and export to W3C web annotation, the same fragment looks like this

```
[
    {
        "@context": "http://www.w3.org/ns/anno.jsonld",
        "id": "urn:nl-mpi-tools-elan-eaf:31dfcd24-e04c-4e75-b698-a91af6925b39#collection1",
        "type": "AnnotationCollection",
        "label": "Tier 1",
        "creator": "John Bell",
        "total": 1,
        "first": {
            "id": "urn:nl-mpi-tools-elan-eaf:31dfcd24-e04c-4e75-b698-a91af6925b39#collection1Page1",
            "type": "AnnotationPage",
            "startIndex": 0,
            "items": [
                {
                    "id": "http://example.com/annotations/195",
                    "type": "Annotation",
                    "body": {
                        "value": "Example",
                        "format": "text/plain",
                        "type": "TextualBody"
                    },
                    "target": {
                        "id": "http://mediaecology.dartmouth.edu/other/KTLAEulaLove.mp4",
                        "type": "Video",
                        "selector": {
                            "conformsTo": "http://www.w3.org/TR/media-frags/",
                            "type": "FragmentSelector",
                            "value": "t=2.019,13.007"
                        }
                    }
                }
            ]
        }
    }
]
```

### What happens on import?

| W3C field | Has equivalent in EAF | Actions on import  |
| ------------- |:-------------:| -----:|
| AnnotationCollection | yes | converts to Tier |
| AnnotationCollection.id | no | will be ignored (the Tier.name is also the id of the tier currently) |
| AnnotationCollection.label | yes | will become Tier.name |
| AnnotationCollection.creator.type | no | will be ignored |
| AnnotationCollection.creator.nickname | yes | will become Tier.annotator |
| AnnotationCollection.creator.email_sha1 | no | will be ignored |
| AnnotationCollection.AnnotationPage | no | all AnnotationPages of an AnnotationCollection will be concatenated |
| AnnotationCollection.AnnotationPage.id | no | will be ignored |
| AnnotationCollection.AnnotationPage.id | no | will be ignored |
| Annotation | yes | converts to (Alignable)Annotation |
| Annotation.id | yes | will become Annotation.ID (XML type ID, so issues with certain characters)|
| Annotation.created | no | will be ignored |
| Annotation.generated | no | will be ignored |
| Annotation.motivation | no | will be ignored |
| Annotation.rights | no | will be ignored, there is a License element on document level |
| Annotation.creator | no | will be ignored |
| Annotation.generator | no | will be ignored |
| Annotation.body.id | no | will be ignored |
| Annotation.body.value | yes | will be converted to Annotation.Value (child element)|
| Annotation.body.language | yes | will be converted to Annotation.ContentLanguage (not implemented yet) |
| Annotation.body.purpose | no | will be ignored |
| Annotation.body.format | no | will be ignored, unicode text is assumed |
| Annotation.body.type | no | TextualBody will be assumed, otherwise the body is ignored |
| Annotation.target.id | yes | converts to MediaDescriptor.MediaURL, on document level |
| Annotation.target.type | yes | converts to MediaDescriptor.MimeType, roughly |
| Annotation.target.selector.type | yes | "FragmentSelector" will be assumed, otherwise the target is ignored |
| Annotation.target.selector.value | yes | begin time and end time will be extracted from the value |

### What happens on export?

When we now export the file from ELAN to W3C web annotation, (most of) the imported information (which is a subset of the original data) can be exported again.
