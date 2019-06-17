
## Media suite example annotation

```
 {
 	"id": "an-f4fc9740-16d6-41e7-a260-90886b6c32bc",
    "created": "2018-07-10T07:42:50Z",
    "modified": "2018-07-10T08:17:37Z",
    "user": "clariah_test",
    "project": "2951cacc-8721-4b34-b8ee-664057d4584d",
    "body": [
        {
        	"annotationId": "eb659a23-9e7e-4776-b490-fde677a51475",
        	"annotationType": "comment",
            "created": "2018-07-10T07:42:50Z",
            "user": "clariah_test",
            "text": "track1"
        },
        {
        	"annotationId": "5cf9556d-3415-49b2-b99d-5aeccc85bbb0",
            "annotationType": "classification",
            "created": "2018-07-10T08:17:37Z",
            "user": "clariah_test",
            "vocabulary": "GTAA",
            "label": "aardewerk",
            "id": "http://data.beeldengeluid.nl/gtaa/28657"
        },
        {
        	"annotationId": "6c7f4521-c863-4483-abb1-ae53c1f00409",
            "annotationType": "link",
            "created": "2018-07-10T08:17:37Z",
            "user": "clariah_test",
            "url": "http://www.nu.nl",
            "label": "test link"
        },
        {
        	"annotationId": "0d638b15-6476-40f7-9dd0-fe2e9fb12e73",
            "annotationType": "metadata",
            "created": "2018-07-10T08:17:37Z",
            "user": "clariah_test",
            "annotationTemplate": "generic",
            "properties": [
                {
                    "value": "Een interessant programma",
                    "key": "title"
                },
                {
                    "value": "We kijken met plezier",
                    "key": "description"
                },
                {
                    "value": "1980-03-04",
                    "key": "date"
                }
            ]
        }
    ],
    "target": {
        "assetId": "ACTTWEEVANDAA-HRE0003FE45",
        "source": "http://play-proxy.clariah.nl/api/play/beng-video/65FG4111FSI.BBEOBWFFXUUDB",
        "type": "Segment",
        "selector": {
            "type": "NestedPIDSelector",
            "value": [
                {
                    "property": "isPartOf",
                    "type": [
                        "Collection"
                    ],
                    "id": "nisv-catalogue-aggr-full-18-158"
                },
                {
                    "property": "isPartOf",
                    "type": [
                        "Resource"
                    ],
                    "id": "50263@program"
                },
                {
                    "property": "isRepresentation",
                    "type": [
                        "Representation",
                        "MediaObject",
                        "Video",
                        "Segment"
                    ],
                    "id": "ACTTWEEVANDAA-HRE0003FE45"
                }
            ],
            "refinedBy": {
                "conformsTo": "http://www.w3.org/TR/media-frags/",
                "start": 1369.024871,
                "end": 1429.976665,
                "value": "#t=1369.024871,1429.976665",
                "type": "FragmentSelector"
            }
        }
    }
}

```


## Importing between W3C & the media suite

### What happens on import?

| W3C field not in MS | Present in W3C | Actions on import  |
| ------------- |:-------------:| -----:|
| motivation ("highlighting") | yes | will be ignored |
| creator object | yes | requires mapping to user field |
| body.type | yes | will be ignored |
| body.format | yes | will be ignored |
| body.language | yes | will be ignored |
| body.value | yes | requires mapping to body.text |
| body.purpose | yes | requires mapping to body.annotationType = “comment” |


| MS field not in W3C | Present in W3C | Actions on import |
| ------------- |:-------------:| -----:|
| body.annotationId | no | will be generated |
| body.user | no | will be mapped from creator |
| body.annotationType | no | will be mapped from body.purpose |
| body.created | yes | will be set to time of import |


After performing the actions stated in the above tables the annotation can be succesfully imported into the MS in the form of a "comment" annotation.

### What happens on export?

When we now add an extra comment in the MS and then export to W3C the following applies:

| W3C field not in MS | Present in W3C | Actions on export |
| ------------- |:-------------:| -----:|
| motivation ("highlighting") | yes | will not be generated
| creator object | yes | will be generated as such: creator.type = Person; creator.nickname = user.name |
| body.type | yes | will be generated to comply with W3C |
| body.format | yes | will be generated to comply with W3C |
| body.language | yes | will be generated to comply with W3C |
| body.value | yes | requires mapping from  body.text |
| body.purpose | yes | requires mapping from body.annotationType = “comment” |