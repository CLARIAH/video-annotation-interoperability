
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