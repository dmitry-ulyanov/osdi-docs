---
layout: default
title: Scripts
---

# Script

This page defines the Script resource.

Scripts are collections of [Questions](questions.html) asked to a person during [Effort](effort.html). 

### Sections

* [Endpoints and URL structures](#endpoints-and-url-structures)
* [Fields](#fields)
    * [Common Fields](#common-fields)
    * [Script Fields](#script-fields) 
    * [Links](#links)
* [Related Resources](#related-resources)
* [Scenarios](#scenarios)
    * [Scenario: Retrieving a collection of Script resources (GET)](#scenario-retrieving-a-collection-of-script-resources-get)
    * [Scenario: Retrieving an individual Script resource (GET)](#scenario-retrieving-an-individual-script-resource-get)
    * [Scenario: Creating a new scipt (POST)](#scenario-creating-a-new-script-post)
    * [Scenario: Modifying a script (PUT)](#scenario-modifying-a-script-put)
    * [Scenario: Deleting a script (DELETE)](#scenario-deleting-a-script-delete)


{% include endpoints_and_url_structures.md %}

The link relation label for a Script resource is ```osdi:script``` for a single Script resource or ```osdi:scripts``` for a collection of Script resources.

_[Back to top...](#)_


## Fields

{% include fields_intro.md %}

{% include global_fields.md %}

_[Back to top...](#)_

### Script Fields

| Name          | Type                | Description
| -----------   | -----------         | --------------
|origin_system      |string     |A human readable identifier of the system where this script was created. (ex: "OSDI System")
|name               |string     |The name of the script. Intended for administrative display rather than a public title, though may be shown to a user.
|title              |string     |The title of the script. Intended for public display rather than administrative purposes.
|description        |string     |A description of the script, usually displayed publicly. May contain text and/or HTML.
|summary            |string     |A text-only single paragraph summarizing the script. Shown on listing pages that have more than titles, but not enough room for full description.

_[Back to top...](#)_

### Links

{% include links_intro.md %}

| Name          | Type       | Description
|-----------    |----------- |-----------
|self           |[Script*](scripts.html)    |A self-referential link to the script.
|creator        |[Person*](people.html)         |A link to a single Person resource representing the creator of the question.
|modified_by    |[Person* ](people.html)        |A link to a Person resource representing the last editor of this question.
|script_questions  |[ScriptQuestion[]*](script_questions.html)  |A link to the collection of Script Question resources for this script.

_[Back to top...](#)_


## Related Resources

* [Person](people.html)
* [Question](questions.html)




_[Back to top...](#)_


## Scenarios

{% include scenarios_intro.md %}

### Scenario: Retrieving a collection of Script resources (GET)

Script resources are sometimes presented as collections of scripts. For example, calling the scripts endpoint will return a collection of all the scripts stored in the system's database associated with your api key.

#### Request

```javascript
GET https://osdi-sample-system.org/api/v1/scripts/

Header:
OSDI-API-Token:[your api key here]
```

#### Response

```javascript
200 OK

Content-Type: application/hal+json
Cache-Control: max-age=0, private, must-revalidate

{
    "total_pages": 10,
    "per_page": 25,
    "page": 1,
    "total_records": 250,
    "_links": {
        "next": {
            "href": "https://osdi-sample-system.org/api/v1/scripts?page=2"
        },
        "osdi:scripts": [
            {
                "href": "https://osdi-sample-system.org/api/v1/scipts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0bc3"
            },
            {
                "href": "https://osdi-sample-system.org/api/v1/scipts/a91b4b2e-ae0e-4cd3-9ed7-d0ec501b0bc3"
            },
            {
                "href": "https://osdi-sample-system.org/api/v1/scipts/1efc3644-af25-4253-90b8-a0baf12dbd1e"
            },
            //(truncated for brevity)
        ],
        "curies": [
            {
                "name": "osdi",
                "href": "https://osdi-sample-system.org/docs/v1/{rel}",
                "templated": true
            }
        ],
        "self": {
            "href": "https://osdi-sample-system.org/api/v1/scipts"
        }
    },
    "_embedded": {
        "osdi:scipts": [
            {
                "identifiers": [
                    "osdi_sample_system:d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa",
                    "foreign_system:1"
                ],
                "origin_system": "OSDI Sample System",
                "created_date": "2014-03-20T21:04:31Z",
                "modified_date": "2014-03-20T21:04:31Z",
                "name": "Script 1",
                "title": "Persuasion Script",
                "description": "<p>Persuasion Script for Area A</p>",
                "summary": "Persuasion Script for Area A"
                "_links": {
                    "self": {
                        "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa"
                    },
                    "osdi:creator": {
                        "href": "https://osdi-sample-system.org/api/v1/people/65345d7d-cd24-466a-a698-4a7686ef684f"
                    },
                    "osdi:modified_by": {
                        "href": "https://osdi-sample-system.org/api/v1/people/c945d6fe-929e-11e3-a2e9-12313d316c29"
                    },
                    "osdi:script_questions" : {
                            "href": "https://osdi-sample-system.org/api/v1/script/c945d6fe-929e-11e3-a2e9/script_questions"
                    }
                },
                {
                    "identifiers": [
                        "osdi_sample_system:d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa",
                        "foreign_system:1"
                    ],
                    "origin_system": "OSDI Sample System",
                    "created_date": "2014-03-20T21:04:31Z",
                    "modified_date": "2014-03-20T21:04:31Z",
                    "name": "Script 1",
                    "title": "Persuasion Script",
                    "description": "<p>Persuasion Script for Area A</p>",
                    "summary": "Persuasion Script for Area A",
                    "_links": {
                        "self": {
                            "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa"
                        },
                        "osdi:creator": {
                            "href": "https://osdi-sample-system.org/api/v1/people/65345d7d-cd24-466a-a698-4a7686ef684f"
                        },
                        "osdi:modified_by": {
                            "href": "https://osdi-sample-system.org/api/v1/people/c945d6fe-929e-11e3-a2e9-12313d316c29"
                        },
                        "osdi:script_questions" : {
                                "href": "https://osdi-sample-system.org/api/v1/script/c945d6fe-929e-11e3-a2e9/script_questions"
                        }
                    }
                }
            },
            //truncated for brevity
        ]
    }
}
``` 

_[Back to top...](#)_       

### Scenario: Retrieving an individual Script resource (GET)

Calling an individual Script resource will return the resource directly, along with all associated fields, embedded Questions and appropriate links to additional information about the script.

#### Request

```javascript
GET https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa

Header:
OSDI-API-Token:[your api key here]
```

#### Response

```javascript
200 OK

Content-Type: application/hal+json
Cache-Control: max-age=0, private, must-revalidate
{
    "identifiers": [
        "osdi_sample_system:d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa",
        "foreign_system:1"
    ],
    "origin_system": "OSDI Sample System",
    "created_date": "2014-03-20T21:04:31Z",
    "modified_date": "2014-03-20T21:04:31Z",
    "name": "Script 1",
    "title": "Persuasion Script",
    "description": "<p>Persuasion Script for Area A</p>",
    "summary": "Persuasion Script for Area A",
    "_links": {
        "self": {
            "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa"
        },
        "osdi:creator": {
            "href": "https://osdi-sample-system.org/api/v1/people/65345d7d-cd24-466a-a698-4a7686ef684f"
        },
        "osdi:modified_by": {
            "href": "https://osdi-sample-system.org/api/v1/people/c945d6fe-929e-11e3-a2e9-12313d316c29"
        },
        "osdi:script_questions" : {
                "href": "https://osdi-sample-system.org/api/v1/scripts/c945d6fe-929e-11e3-a2e9/script_questions"
        }
    },
    "_embedded": {
        "osdi:script_questions": [
          {
            "sequence": 1,
            "_links": {
                "curies": [
                    {
                        "name": "osdi",
                        "href": "https://osdi-sample-system.org/docs/v1/{rel}",
                        "templated": true
                    }
                ],
                "self": {
                    "href": https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3/script_questions/ae0e-4cd3-9ed7-d0
                },
                "osdi:question": {
                  "href": "http://osdi-sample-system.org/api/v1/questions/202004"
                },
                "osdi:script": {
                    "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3"
                }
            },
            "_embedded": {
              "osdi:question":
                {
                  "origin_system": "OSDISystem",
                  "name": "foobar",
                  "description": "What is your name?",
                  "title": "foobar",
                  "summary": "What is your name?",
                  "question_type": "SingleChoice",
                  "identifiers": [
                    "OSDISystem:202004"
                  ],
                  "_links": {
                    "self": {
                      "href": "http://osdi-sample-system.org/api/v1/questions/202004"
                    },
                    "curies": [
                      {
                        "name": "osdi",
                        "href": "http://osdi-sample-system.org/osdi#{rel}",
                        "templated": true
                      }
                    ]
                  }
                }
            }
          },
          {
            "sequence": 2,
            "_links": {
                "curies": [
                    {
                        "name": "osdi",
                        "href": "https://osdi-sample-system.org/docs/v1/{rel}",
                        "templated": true
                    }
                ],
                "self": {
                    "href": https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3/script_questions/be0e-4cd3-9ed7-d0
                },
                "osdi:question": {
                  "href": "http://osdi-sample-system.org/api/v1/questions/203079"
                },
                "osdi:script": {
                    "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3"
                }
            },
            "_embedded": {
              "osdi:question": 
                {
                  "origin_system": "OSDISystem",
                  "name": "pbank",
                  "description": "Will you phone bank?",
                  "title": "pbank",
                  "summary": "Will you phone bank?",
                  "question_type": "SingleChoice",
                  "responses": [
                    {
                      "key": "856278",
                      "name": "Yes",
                      "title": "Yes"
                    },
                    {
                      "key": "856279",
                      "name": "No",
                      "title": "No"
                    }
                  ],
                  "identifiers": [
                    "OSDISystem:203079"
                  ],
                  "_links": {
                    "self": {
                      "href": "http://osdi-sample-system.org/api/v1/questions/203079"
                    },
                    "curies": [
                      {
                        "name": "osdi",
                        "href": "http://osdi-sample-system.org/osdi#{rel}",
                        "templated": true
                      }
                    ]
                  }
                }
            }
          },
          {
            "sequence": 3,
            "_links": {
                "curies": [
                    {
                        "name": "osdi",
                        "href": "https://osdi-sample-system.org/docs/v1/{rel}",
                        "templated": true
                    }
                ],
                "self": {
                    "href": https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3/script_questions/ce0e-4cd3-9ed7-d0
                },
                "osdi:question": {
                  "href": "http://osdi-sample-system.org/api/v1/questions/52472"
                },
                "osdi:script": {
                    "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ecb0bc3"
                }
            },
            "_embedded": {
              "osdi:question":
                {
                  "origin_system": "OSDISystem",
                  "question_type": "SingleChoice",
                  "identifiers": [
                    "OSDISystem:52472"
                  ],
                  "_links": {
                    "self": {
                      "href": "http://osdi-sample-system.org/api/v1/questions/52472"
                    },
                    "curies": [
                      {
                        "name": "osdi",
                        "href": "http://osdi-sample-system.org/osdi#{rel}",
                        "templated": true
                      }
                    ]
                  }
                }
            }
          },
          // truncated for brevity
        ]
    }
}
```


_[Back to top...](#)_


### Scenario: Creating a new script (POST)

Posting to the script collection endpoint will allow you to create a new script. The response is the new script that was created. While each implementing system will require different fields, any optional fields not included in a post operation should not be set at all by the receiving system, or should be set to default values.

#### Request

```javascript
POST https://osdi-sample-system.org/api/v1/scripts/

Header:
OSDI-API-Token:[your api key here]

{
    "identifiers": [
        "foreign_system:1"
    ],
    "name": "Script 1",
    "title": "Persuasion Script",
    "description": "<p>Persuasion Script for Area A</p>",
    "summary": "Persuasion Script for Area A",
}

```

#### Response

```javascript
200 OK

Content-Type: application/hal+json
Cache-Control: max-age=0, private, must-revalidate
{
    "identifiers": [
        "osdi_sample_system:d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa",
        "foreign_system:1"
    ],
    "origin_system": "OSDI Sample System",
    "created_date": "2014-03-20T21:04:31Z",
    "modified_date": "2014-03-20T21:04:31Z",
    "name": "Script 1",
    "title": "Persuasion Script",
    "description": "<p>Persuasion Script for Area A</p>",
    "summary": "Persuasion Script for Area A",
    "_links": {
        "self": {
            "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa"
        },
        "osdi:creator": {
            "href": "https://osdi-sample-system.org/api/v1/people/65345d7d-cd24-466a-a698-4a7686ef684f"
        },
        "osdi:modified_by": {
            "href": "https://osdi-sample-system.org/api/v1/people/c945d6fe-929e-11e3-a2e9-12313d316c29"
        },
       "osdi:script_questions": {
            "href": "https://osdi-sample-system.org/api/v1/scripts/c945d6fe-929e-11e3-a2e9/script_questions"
        }
}
```

_[Back to top...](#)_


### Scenario: Modifying a scipt (PUT)

You can update a script by calling a PUT operation on that script's endpoint. Your PUT should contain fields that you want to update. Missing fields will be ignored by the receiving system. Systems may also ignore PUT values, depending on whether fields you are trying to modify are read-only or not. You may set an attribute to nil by including the attribute using `nil` for value.

{% include array_warning.md %}

#### Request

```javascript
PUT https://osdi-sample-system.org/api/v1/scipts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa

Header:
OSDI-API-Token:[your api key here]

{
    "name": "Script 1",
    "title": "Persuasion Script"
}

```

#### Response
```javascript
200 OK

Content-Type: application/hal+json
Cache-Control: max-age=0, private, must-revalidate
{
    "identifiers": [
        "osdi_sample_system:d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa",
        "foreign_system:1"
    ],
    "origin_system": "OSDI Sample System",
    "created_date": "2014-03-20T21:04:31Z",
    "modified_date": "2014-03-20T21:04:31Z",
    "name": "Script 1",
    "title": "Persuasion Script",
    "description": "<p>Persuasion Script for Area A</p>",
    "summary": "Persuasion Script for Area A",
    "_links": {
        "self": {
            "href": "https://osdi-sample-system.org/api/v1/scripts/d91b4b2e-ae0e-4cd3-9ed7-d0ec501b0baa"
        },
        "osdi:creator": {
            "href": "https://osdi-sample-system.org/api/v1/people/65345d7d-cd24-466a-a698-4a7686ef684f"
        },
        "osdi:modified_by": {
            "href": "https://osdi-sample-system.org/api/v1/people/c945d6fe-929e-11e3-a2e9-12313d316c29"
        },
        "osdi:script_questions": {
                "href": "https://osdi-sample-system.org/api/v1/scripts/c945d6fe-929e-11e3-a2e9/script_questions"
        }
}
```


_[Back to top...](#)_


### Scenario: Deleting a scipt (DELETE)

You may delete a script by calling the DELETE command on the script's endpoint.

#### Request

```javascript
DELETE https://osdi-sample-system.org/api/v1/scripts/d32fcdd6-7366-466d-a3b8-7e0d87c3cd8b

Header:
OSDI-API-Token:[your api key here]
```

#### Response

```javascript
200 OK

Content-Type: application/hal+json
Cache-Control: max-age=0, private, must-revalidate

{
    "notice": "This script was successfully deleted."
}
```

_[Back to top...](#)_