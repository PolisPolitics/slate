# Surveys

## The Survey object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated securitygroup
customerId | true | Identifier of the associated customer
data | true | Surveys data

### data

Attribute | Required? | Description
--------- | --------- | -----------
discoverable | false | Boolean value that allow a survey to be shared between organizations. Default value is `false`
name | true | Name of the survey
questionFlow | false | The flow of questions in this survey
questions | true | Array of questions. [details](#data-questions)

### data/questions
Array of the following:

Attribute | Required? | Description
--------- | --------- | -----------
questionId | true | Identifier of the question.
actions | true | Array of actions that can be taken for this question. [details](#data-questions-actions)

### data/questions/actions
Array of the following:

Attribute | Required? | Description
--------- | --------- | -----------
questionId | true | Identifier of the question.
type | true | Allowed values ['question', 'end', 'pdf', 'edit'].
icon | true | Name of the icon. Should be one `faceNeutral`, `faceHappy`, `faceSad`, `faceHappiest`, `faceSaddest`,
  `yes`, `no`, `questionMark`.


### questions
Attribute | Required? | Description
--------- | --------- | -----------
text | true | Text of the question. Max 512 characters.
tag | true | Short description or identifier of the question. 128 chars max.
required | false | Flag indicating whether question is required. Default `false`.
criteria | true | Object that defines the criteria used to analyze the contacts. [details](#data-criteria)
questionId | false | Unique Identifier for this question.

### data/criteria

Attribute | Required? | Description
--------- | --------- | -----------
filter | true | Can be `any` or `all`.
clauses | true | Specifies something. Minimum 1 clause. [details](#data-criteria-clause)

### data/criteria/clause

Attribute | Required? | Description
--------- | --------- | -----------
source | true | Path to the contact attribute.
operator | true | Operator used to compare the value and the contact attribute retrieved using the source path. Can be `eq`, `neq`, `gt`, `gte`, `lt`, `lte` or `in`.
value | true | Value used for comparison.

For each type of question the option object will change and it may be that more attributes are added to the option.

Types:
#### availability

Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 2 options.

#### multi-choice

Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 2 options.
type | true | Type of questions. Allowed values `availability`, `multiChoice`, `payment`.

#### multi-select
Attribute | Required? | Description
--------- | --------- | -----------
type | true | Type of questions. Allowed values `multiSelect`.
options | true | Array of possible options. Minimum of 1 options.
choices | true | Array of possible choices. Minimum of 1 choice. [details](#choice-object)

#### pdf
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 2 options.
url | true | String containing the url to the pdf.
type | true | Type of questions. Allowed values `pdf`.

#### scale
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 5 options.
type | true | Type of questions. Allowed values `scale`.

#### text
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 2 options.
multiline | false | Defines if the text input is multiline. Default value is `false`.
max | false | Max size of the input string. Default `256`.
keyboard | false | Type of input. Can be `text`, `email`, `number`. Default value is `text`.
placeholder | false | Input placeholder. Default is an empty string.
type | true | Type of questions. Allowed values `text`.

#### verification
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 1 options and maximum of 2 options.
type | true | Type of questions. Allowed values `verification`.

#### youtube
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 1 options and maximum of 2 options.
url | true | String containing the url to the youtube video.
type | true | Type of questions. Allowed values `youtube`.

### Choice Object

The `icon` or `text` is required.

Attribute | Required? | Description
--------- | --------- | -----------
text | false | Description text of the option. 128 characters max.
icon | false | Icon that will appear on the app. Can be `face-neutral`, `face-happy`, `face-sad`, `face-happiest`, `face-saddest`, `yes`, `no` or `questionmark`.
tag | false | Tag of the option.
success | false | Makes this option a success if `true`. By default is set to `false`.
value | false | Value of the option. Must be a string or a number.

### Option Object

The `icon` or `text` is required.

Attribute | Required? | Description
--------- | --------- | -----------
text | false | Description text of the option. 128 characters max.
icon | false | Icon that will appear on the app. Can be `face-neutral`, `face-happy`, `face-sad`, `face-happiest`, `face-saddest`, `yes`, `no` or `questionmark`.
tag | false | Tag of the option.
success | false | Makes this option a success if `true`. By default is set to `false`.
value | false | Value of the option. Must be a string or a number.
action | false | Action executed if the option is selected. [details](#action-object)

### Action Object

The action object is used to define the order of questions of a survey.
When an option of a question is selected, if it's action equals to `question` then next question will be called and if it's action type equals to `end`, the survey will finish.

Attribute | Required? | Description
--------- | --------- | -----------
type | false | Type of action that will be executed. Can be one out of `question`, `pdf`, `end` or `edit`.
questionId | false | Identifier of the next question.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "76a86650-5524-4634-bbad-ad52f5237f7d",
	"data": {
		"name": "Default Survey",
		"questions": [
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6",
						"questionOptionId": "e4f57754-9348-4abe-8bae-ae820dc9f252"
					},
					{
						"icon": "yes",
						"type": "question",
						"questionId": "83439622-cf55-4f0d-a7da-046862b73761",
						"questionOptionId": "ee3417b4-e644-499e-9aae-54424818f5aa"
					}
				],
				"questionId": "fea9b266-3def-4d4e-89fd-824bfed902a3"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "1471c7f2-f881-4841-a066-55c8210eb000"
					},
					{
						"type": "end",
						"questionOptionId": "51c75a1d-e424-4580-ba28-434ed65fbc4f"
					},
					{
						"type": "end",
						"questionOptionId": "5322941d-0ff9-475f-b545-498fd102ce9a"
					},
					{
						"type": "end",
						"questionOptionId": "5d97bbbe-7ab4-46e3-beea-afa7f631b038"
					},
					{
						"type": "end",
						"questionOptionId": "be2fbcc1-acf9-4411-a97b-92c14aaa3d77"
					},
					{
						"type": "end",
						"questionOptionId": "d784faec-3a21-4edc-8f2d-05b484251994"
					},
					{
						"type": "end",
						"questionOptionId": "fae56419-dbaf-4439-8062-cd5be748e17b"
					}
				],
				"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "b36e32b1-1b0a-4ec6-a945-f56fa61f051c"
					},
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "578ef90b-df35-42f2-befc-6c7d19f956e4"
					}
				],
				"questionId": "83439622-cf55-4f0d-a7da-046862b73761"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "0e21abce-fe32-4353-91cc-5bac307fd293"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "c3f42d6d-7a28-4f44-b11f-1fae28113584"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "87d31382-88ba-4540-b754-6e3e4dccb254"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "5a92928b-4f27-4a37-abcc-0f0b49081b19"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "96660749-a57f-47bd-8774-bc8ca3ee6e52"
					}
				],
				"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					}
				],
				"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					}
				],
				"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Confirm",
						"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
					}
				],
				"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
					}
				],
				"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
					}
				],
				"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "5b17d78c-9f36-4d84-ad9f-f3a29fc5d45d"
					},
					{
						"type": "end",
						"questionOptionId": "50092030-dbf5-4b45-a827-c17571ce5405"
					},
					{
						"type": "end",
						"questionOptionId": "60208cd2-0fd5-4cb3-9cba-0a2b6c34da12"
					}
				],
				"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
			}
		],
		"discoverable": false
	},
	"meta": {
		"created": "2019-04-03T18:55:28.721Z",
		"modified": "2019-04-03T18:55:29.991Z",
		"resource": "surveys",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many surveys

> Example Request

```http
GET /surveys?filter%5B%2Fdata%2Fdiscoverable%5D=false&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "76a86650-5524-4634-bbad-ad52f5237f7d",
			"data": {
				"name": "Default Survey",
				"questions": [
					{
						"actions": [
							{
								"icon": "no",
								"type": "question",
								"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6",
								"questionOptionId": "e4f57754-9348-4abe-8bae-ae820dc9f252"
							},
							{
								"icon": "yes",
								"type": "question",
								"questionId": "83439622-cf55-4f0d-a7da-046862b73761",
								"questionOptionId": "ee3417b4-e644-499e-9aae-54424818f5aa"
							}
						],
						"questionId": "fea9b266-3def-4d4e-89fd-824bfed902a3"
					},
					{
						"actions": [
							{
								"type": "end",
								"questionOptionId": "1471c7f2-f881-4841-a066-55c8210eb000"
							},
							{
								"type": "end",
								"questionOptionId": "51c75a1d-e424-4580-ba28-434ed65fbc4f"
							},
							{
								"type": "end",
								"questionOptionId": "5322941d-0ff9-475f-b545-498fd102ce9a"
							},
							{
								"type": "end",
								"questionOptionId": "5d97bbbe-7ab4-46e3-beea-afa7f631b038"
							},
							{
								"type": "end",
								"questionOptionId": "be2fbcc1-acf9-4411-a97b-92c14aaa3d77"
							},
							{
								"type": "end",
								"questionOptionId": "d784faec-3a21-4edc-8f2d-05b484251994"
							},
							{
								"type": "end",
								"questionOptionId": "fae56419-dbaf-4439-8062-cd5be748e17b"
							}
						],
						"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6"
					},
					{
						"actions": [
							{
								"type": "question",
								"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
								"questionOptionId": "b36e32b1-1b0a-4ec6-a945-f56fa61f051c"
							},
							{
								"type": "question",
								"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
								"questionOptionId": "578ef90b-df35-42f2-befc-6c7d19f956e4"
							}
						],
						"questionId": "83439622-cf55-4f0d-a7da-046862b73761"
					},
					{
						"actions": [
							{
								"type": "question",
								"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
								"questionOptionId": "0e21abce-fe32-4353-91cc-5bac307fd293"
							},
							{
								"type": "question",
								"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
								"questionOptionId": "c3f42d6d-7a28-4f44-b11f-1fae28113584"
							},
							{
								"type": "question",
								"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
								"questionOptionId": "87d31382-88ba-4540-b754-6e3e4dccb254"
							},
							{
								"type": "question",
								"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
								"questionOptionId": "5a92928b-4f27-4a37-abcc-0f0b49081b19"
							},
							{
								"type": "question",
								"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
								"questionOptionId": "96660749-a57f-47bd-8774-bc8ca3ee6e52"
							}
						],
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577"
					},
					{
						"actions": [
							{
								"icon": "no",
								"type": "question",
								"optionText": "Cancel",
								"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
							},
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
							}
						],
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b"
					},
					{
						"actions": [
							{
								"icon": "no",
								"type": "question",
								"optionText": "Cancel",
								"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
							},
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
							}
						],
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Confirm",
								"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
							}
						],
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
							}
						],
						"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
							}
						],
						"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
					},
					{
						"actions": [
							{
								"type": "end",
								"questionOptionId": "5b17d78c-9f36-4d84-ad9f-f3a29fc5d45d"
							},
							{
								"type": "end",
								"questionOptionId": "50092030-dbf5-4b45-a827-c17571ce5405"
							},
							{
								"type": "end",
								"questionOptionId": "60208cd2-0fd5-4cb3-9cba-0a2b6c34da12"
							}
						],
						"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
					}
				],
				"discoverable": false
			},
			"meta": {
				"created": "2019-04-03T18:55:28.721Z",
				"modified": "2019-04-03T18:55:29.991Z",
				"resource": "surveys",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "a1a61b83-0697-4354-a64b-59a9f64cd5d2",
			"data": {
				"name": "Default Survey",
				"questions": [
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"questionId": "4f70354f-f569-4993-8814-a895ebbf6904",
								"questionOptionId": "c4ecd514-624e-4b01-9b3e-d53df5e327e5"
							},
							{
								"icon": "no",
								"type": "question",
								"questionId": "9445d976-fa58-4e3b-853c-8d7d9b3ab665",
								"questionOptionId": "f936b287-7a6e-4bd8-a981-32814169aec0"
							}
						],
						"questionId": "3f0757f5-8ff3-44f2-b634-d01e0cc54143"
					},
					{
						"actions": [
							{
								"type": "end",
								"questionOptionId": "0edef130-0271-4b77-908b-ecf9cdb3a4c1"
							},
							{
								"type": "end",
								"questionOptionId": "16a141aa-1b24-46e8-abe1-5c2321943581"
							},
							{
								"type": "end",
								"questionOptionId": "43227576-c4c0-483d-bab9-300bcd9b8f35"
							},
							{
								"type": "end",
								"questionOptionId": "453b0b04-556b-4cc8-87bc-db4c7654e76e"
							},
							{
								"type": "end",
								"questionOptionId": "7d68ea6e-d32d-4867-aa4b-0e9a1de5c45a"
							},
							{
								"type": "end",
								"questionOptionId": "a1468bd6-5ed1-4616-8efb-4783907a56bb"
							},
							{
								"type": "end",
								"questionOptionId": "e3033b72-300a-4b22-ae4b-688e87a50217"
							}
						],
						"questionId": "9445d976-fa58-4e3b-853c-8d7d9b3ab665"
					},
					{
						"actions": [
							{
								"type": "question",
								"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8",
								"questionOptionId": "b8701ab0-812f-488e-8985-474f86725cb2"
							},
							{
								"type": "question",
								"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8",
								"questionOptionId": "907e13e5-ae0e-408d-b834-1ff6a0dc467e"
							}
						],
						"questionId": "4f70354f-f569-4993-8814-a895ebbf6904"
					},
					{
						"actions": [
							{
								"type": "question",
								"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
								"questionOptionId": "f04ce726-2ae3-4ddd-96bd-48739c29ba4c"
							},
							{
								"type": "question",
								"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
								"questionOptionId": "cc155424-9296-433b-8bfc-f7e5f4f8a1b8"
							},
							{
								"type": "question",
								"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
								"questionOptionId": "8db71633-0576-4422-9d0d-27059520d8b3"
							},
							{
								"type": "question",
								"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
								"questionOptionId": "213581f6-d369-413f-8824-a76e6cccfaf2"
							},
							{
								"type": "question",
								"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
								"questionOptionId": "7801e142-78bb-4b8d-898e-ff9826c396da"
							}
						],
						"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8"
					},
					{
						"actions": [
							{
								"icon": "no",
								"type": "question",
								"optionText": "Cancel",
								"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
							},
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
							}
						],
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762"
					},
					{
						"actions": [
							{
								"icon": "no",
								"type": "question",
								"optionText": "Cancel",
								"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
							},
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
							}
						],
						"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Confirm",
								"questionId": "51402915-6bb6-420f-9c53-3309d00b7a76"
							}
						],
						"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "b4d92723-d1d6-4b99-9ff4-75b622b6e3d8"
							}
						],
						"questionId": "51402915-6bb6-420f-9c53-3309d00b7a76"
					},
					{
						"actions": [
							{
								"icon": "yes",
								"type": "question",
								"optionText": "Submit",
								"questionId": "abe83390-8897-4659-b39f-f22623f2f180"
							}
						],
						"questionId": "b4d92723-d1d6-4b99-9ff4-75b622b6e3d8"
					},
					{
						"actions": [
							{
								"type": "end",
								"questionOptionId": "ae2c12f9-b5c9-4f59-b3c8-400fab20e7db"
							},
							{
								"type": "end",
								"questionOptionId": "29c8c38e-a4f9-4d99-a655-5ffbf9afd1dc"
							},
							{
								"type": "end",
								"questionOptionId": "cfffdfb7-cba9-4391-aaa6-54609b0f0b2a"
							}
						],
						"questionId": "abe83390-8897-4659-b39f-f22623f2f180"
					}
				],
				"discoverable": false
			},
			"meta": {
				"etag": "",
				"created": "2019-04-19T18:58:24.963Z",
				"modified": "2019-04-19T18:58:24.963Z",
				"resource": "surveys",
				"createdBy": "1aafa574-82ce-416e-801c-588142cb4824",
				"isDeleted": false,
				"modifiedBy": "1aafa574-82ce-416e-801c-588142cb4824"
			},
			"customerId": "29e66b77-4f40-43c0-b239-1544e16cd4fc",
			"securityGroupId": "95bcaa14-10ff-4a41-90f0-5d98a960dd00"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /surveys`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. `/data/campaignId eq "0cb2dc71-73ba-4eca-977c-548085328521"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a survey

> Example Request

```http
GET /surveys/76a86650-5524-4634-bbad-ad52f5237f7d HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "76a86650-5524-4634-bbad-ad52f5237f7d",
	"data": {
		"name": "Default Survey",
		"questions": [
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6",
						"questionOptionId": "e4f57754-9348-4abe-8bae-ae820dc9f252"
					},
					{
						"icon": "yes",
						"type": "question",
						"questionId": "83439622-cf55-4f0d-a7da-046862b73761",
						"questionOptionId": "ee3417b4-e644-499e-9aae-54424818f5aa"
					}
				],
				"questionId": "fea9b266-3def-4d4e-89fd-824bfed902a3"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "1471c7f2-f881-4841-a066-55c8210eb000"
					},
					{
						"type": "end",
						"questionOptionId": "51c75a1d-e424-4580-ba28-434ed65fbc4f"
					},
					{
						"type": "end",
						"questionOptionId": "5322941d-0ff9-475f-b545-498fd102ce9a"
					},
					{
						"type": "end",
						"questionOptionId": "5d97bbbe-7ab4-46e3-beea-afa7f631b038"
					},
					{
						"type": "end",
						"questionOptionId": "be2fbcc1-acf9-4411-a97b-92c14aaa3d77"
					},
					{
						"type": "end",
						"questionOptionId": "d784faec-3a21-4edc-8f2d-05b484251994"
					},
					{
						"type": "end",
						"questionOptionId": "fae56419-dbaf-4439-8062-cd5be748e17b"
					}
				],
				"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "b36e32b1-1b0a-4ec6-a945-f56fa61f051c"
					},
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "578ef90b-df35-42f2-befc-6c7d19f956e4"
					}
				],
				"questionId": "83439622-cf55-4f0d-a7da-046862b73761"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "0e21abce-fe32-4353-91cc-5bac307fd293"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "c3f42d6d-7a28-4f44-b11f-1fae28113584"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "87d31382-88ba-4540-b754-6e3e4dccb254"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "5a92928b-4f27-4a37-abcc-0f0b49081b19"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "96660749-a57f-47bd-8774-bc8ca3ee6e52"
					}
				],
				"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					}
				],
				"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					}
				],
				"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Confirm",
						"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
					}
				],
				"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
					}
				],
				"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
					}
				],
				"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "5b17d78c-9f36-4d84-ad9f-f3a29fc5d45d"
					},
					{
						"type": "end",
						"questionOptionId": "50092030-dbf5-4b45-a827-c17571ce5405"
					},
					{
						"type": "end",
						"questionOptionId": "60208cd2-0fd5-4cb3-9cba-0a2b6c34da12"
					}
				],
				"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
			}
		],
		"discoverable": false
	},
	"meta": {
		"created": "2019-04-03T18:55:28.721Z",
		"modified": "2019-04-03T18:55:29.991Z",
		"resource": "surveys",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the survey to be retrieved.


## Create a survey.

> Example Request

```http
POST /surveys HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"name": "Default Survey",
		"discoverable": false,
		"questions": [
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6",
						"questionOptionId": "e4f57754-9348-4abe-8bae-ae820dc9f252"
					},
					{
						"icon": "yes",
						"type": "question",
						"questionId": "83439622-cf55-4f0d-a7da-046862b73761",
						"questionOptionId": "ee3417b4-e644-499e-9aae-54424818f5aa"
					}
				],
				"questionId": "fea9b266-3def-4d4e-89fd-824bfed902a3"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "1471c7f2-f881-4841-a066-55c8210eb000"
					},
					{
						"type": "end",
						"questionOptionId": "51c75a1d-e424-4580-ba28-434ed65fbc4f"
					},
					{
						"type": "end",
						"questionOptionId": "5322941d-0ff9-475f-b545-498fd102ce9a"
					},
					{
						"type": "end",
						"questionOptionId": "5d97bbbe-7ab4-46e3-beea-afa7f631b038"
					},
					{
						"type": "end",
						"questionOptionId": "be2fbcc1-acf9-4411-a97b-92c14aaa3d77"
					},
					{
						"type": "end",
						"questionOptionId": "d784faec-3a21-4edc-8f2d-05b484251994"
					},
					{
						"type": "end",
						"questionOptionId": "fae56419-dbaf-4439-8062-cd5be748e17b"
					}
				],
				"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "b36e32b1-1b0a-4ec6-a945-f56fa61f051c"
					},
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "578ef90b-df35-42f2-befc-6c7d19f956e4"
					}
				],
				"questionId": "83439622-cf55-4f0d-a7da-046862b73761"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "0e21abce-fe32-4353-91cc-5bac307fd293"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "c3f42d6d-7a28-4f44-b11f-1fae28113584"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "87d31382-88ba-4540-b754-6e3e4dccb254"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "5a92928b-4f27-4a37-abcc-0f0b49081b19"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "96660749-a57f-47bd-8774-bc8ca3ee6e52"
					}
				],
				"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					}
				],
				"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					}
				],
				"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Confirm",
						"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
					}
				],
				"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
					}
				],
				"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
					}
				],
				"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "5b17d78c-9f36-4d84-ad9f-f3a29fc5d45d"
					},
					{
						"type": "end",
						"questionOptionId": "50092030-dbf5-4b45-a827-c17571ce5405"
					},
					{
						"type": "end",
						"questionOptionId": "60208cd2-0fd5-4cb3-9cba-0a2b6c34da12"
					}
				],
				"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
			}
		]
	},
	"customerId": "f16a1733-f553-4395-bc22-d16d5085a634"
}
```

> Example Response

```json
{
	"id": "76a86650-5524-4634-bbad-ad52f5237f7d",
	"data": {
		"name": "Default Survey",
		"questions": [
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6",
						"questionOptionId": "e4f57754-9348-4abe-8bae-ae820dc9f252"
					},
					{
						"icon": "yes",
						"type": "question",
						"questionId": "83439622-cf55-4f0d-a7da-046862b73761",
						"questionOptionId": "ee3417b4-e644-499e-9aae-54424818f5aa"
					}
				],
				"questionId": "fea9b266-3def-4d4e-89fd-824bfed902a3"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "1471c7f2-f881-4841-a066-55c8210eb000"
					},
					{
						"type": "end",
						"questionOptionId": "51c75a1d-e424-4580-ba28-434ed65fbc4f"
					},
					{
						"type": "end",
						"questionOptionId": "5322941d-0ff9-475f-b545-498fd102ce9a"
					},
					{
						"type": "end",
						"questionOptionId": "5d97bbbe-7ab4-46e3-beea-afa7f631b038"
					},
					{
						"type": "end",
						"questionOptionId": "be2fbcc1-acf9-4411-a97b-92c14aaa3d77"
					},
					{
						"type": "end",
						"questionOptionId": "d784faec-3a21-4edc-8f2d-05b484251994"
					},
					{
						"type": "end",
						"questionOptionId": "fae56419-dbaf-4439-8062-cd5be748e17b"
					}
				],
				"questionId": "b0f2bc7e-3089-401d-afb7-5e6659d0f1e6"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "b36e32b1-1b0a-4ec6-a945-f56fa61f051c"
					},
					{
						"type": "question",
						"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577",
						"questionOptionId": "578ef90b-df35-42f2-befc-6c7d19f956e4"
					}
				],
				"questionId": "83439622-cf55-4f0d-a7da-046862b73761"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "0e21abce-fe32-4353-91cc-5bac307fd293"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "c3f42d6d-7a28-4f44-b11f-1fae28113584"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "87d31382-88ba-4540-b754-6e3e4dccb254"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "5a92928b-4f27-4a37-abcc-0f0b49081b19"
					},
					{
						"type": "question",
						"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b",
						"questionOptionId": "96660749-a57f-47bd-8774-bc8ca3ee6e52"
					}
				],
				"questionId": "2438cc93-4395-4ded-99f0-0a4ac88e2577"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
					}
				],
				"questionId": "510922c1-0a7e-40e1-b329-168b88c6cf3b"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
					}
				],
				"questionId": "940f694b-d8d6-4b40-9f3d-efe9b6b110b5"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Confirm",
						"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
					}
				],
				"questionId": "7e23f830-23a1-42dc-a33b-5617402cd880"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
					}
				],
				"questionId": "eb444550-4f38-43a2-a5c0-6634c3d9a003"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
					}
				],
				"questionId": "60a528b7-1b36-483a-9bdb-65c00b067e62"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "5b17d78c-9f36-4d84-ad9f-f3a29fc5d45d"
					},
					{
						"type": "end",
						"questionOptionId": "50092030-dbf5-4b45-a827-c17571ce5405"
					},
					{
						"type": "end",
						"questionOptionId": "60208cd2-0fd5-4cb3-9cba-0a2b6c34da12"
					}
				],
				"questionId": "77227e62-d098-46b3-985b-a83e19a4850d"
			}
		],
		"discoverable": false
	},
	"meta": {
		"created": "2019-04-03T18:55:28.721Z",
		"modified": "2019-04-03T18:55:29.991Z",
		"resource": "surveys",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST /surveys`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data of the survey to be created


## Update a survey

> Example Request

```http
PATCH /surveys/a1a61b83-0697-4354-a64b-59a9f64cd5d2 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/discoverable",
			"value": true
		}
	]
}
```


<aside class='notice'>
You can only patch attributes inside <b>data</b> key.
</aside>

> Example Response

```json
{
	"id": "a1a61b83-0697-4354-a64b-59a9f64cd5d2",
	"data": {
		"name": "Default Survey",
		"questions": [
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"questionId": "4f70354f-f569-4993-8814-a895ebbf6904",
						"questionOptionId": "c4ecd514-624e-4b01-9b3e-d53df5e327e5"
					},
					{
						"icon": "no",
						"type": "question",
						"questionId": "9445d976-fa58-4e3b-853c-8d7d9b3ab665",
						"questionOptionId": "f936b287-7a6e-4bd8-a981-32814169aec0"
					}
				],
				"questionId": "3f0757f5-8ff3-44f2-b634-d01e0cc54143"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "0edef130-0271-4b77-908b-ecf9cdb3a4c1"
					},
					{
						"type": "end",
						"questionOptionId": "16a141aa-1b24-46e8-abe1-5c2321943581"
					},
					{
						"type": "end",
						"questionOptionId": "43227576-c4c0-483d-bab9-300bcd9b8f35"
					},
					{
						"type": "end",
						"questionOptionId": "453b0b04-556b-4cc8-87bc-db4c7654e76e"
					},
					{
						"type": "end",
						"questionOptionId": "7d68ea6e-d32d-4867-aa4b-0e9a1de5c45a"
					},
					{
						"type": "end",
						"questionOptionId": "a1468bd6-5ed1-4616-8efb-4783907a56bb"
					},
					{
						"type": "end",
						"questionOptionId": "e3033b72-300a-4b22-ae4b-688e87a50217"
					}
				],
				"questionId": "9445d976-fa58-4e3b-853c-8d7d9b3ab665"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8",
						"questionOptionId": "b8701ab0-812f-488e-8985-474f86725cb2"
					},
					{
						"type": "question",
						"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8",
						"questionOptionId": "907e13e5-ae0e-408d-b834-1ff6a0dc467e"
					}
				],
				"questionId": "4f70354f-f569-4993-8814-a895ebbf6904"
			},
			{
				"actions": [
					{
						"type": "question",
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
						"questionOptionId": "f04ce726-2ae3-4ddd-96bd-48739c29ba4c"
					},
					{
						"type": "question",
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
						"questionOptionId": "cc155424-9296-433b-8bfc-f7e5f4f8a1b8"
					},
					{
						"type": "question",
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
						"questionOptionId": "8db71633-0576-4422-9d0d-27059520d8b3"
					},
					{
						"type": "question",
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
						"questionOptionId": "213581f6-d369-413f-8824-a76e6cccfaf2"
					},
					{
						"type": "question",
						"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762",
						"questionOptionId": "7801e142-78bb-4b8d-898e-ff9826c396da"
					}
				],
				"questionId": "2537adb6-2cbd-4f88-af1e-0f35ce10ebc8"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
					}
				],
				"questionId": "c907bbd8-56df-425a-beb4-0b2611bd6762"
			},
			{
				"actions": [
					{
						"icon": "no",
						"type": "question",
						"optionText": "Cancel",
						"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
					},
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
					}
				],
				"questionId": "4ce739cb-6a75-4bb3-952b-ed30278148be"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Confirm",
						"questionId": "51402915-6bb6-420f-9c53-3309d00b7a76"
					}
				],
				"questionId": "26f35c96-ad0b-4474-98b6-4b51ecba33ee"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "b4d92723-d1d6-4b99-9ff4-75b622b6e3d8"
					}
				],
				"questionId": "51402915-6bb6-420f-9c53-3309d00b7a76"
			},
			{
				"actions": [
					{
						"icon": "yes",
						"type": "question",
						"optionText": "Submit",
						"questionId": "abe83390-8897-4659-b39f-f22623f2f180"
					}
				],
				"questionId": "b4d92723-d1d6-4b99-9ff4-75b622b6e3d8"
			},
			{
				"actions": [
					{
						"type": "end",
						"questionOptionId": "ae2c12f9-b5c9-4f59-b3c8-400fab20e7db"
					},
					{
						"type": "end",
						"questionOptionId": "29c8c38e-a4f9-4d99-a655-5ffbf9afd1dc"
					},
					{
						"type": "end",
						"questionOptionId": "cfffdfb7-cba9-4391-aaa6-54609b0f0b2a"
					}
				],
				"questionId": "abe83390-8897-4659-b39f-f22623f2f180"
			}
		],
		"discoverable": true
	},
	"meta": {
		"etag": "",
		"created": "2019-04-19T18:58:24.963Z",
		"modified": "2019-04-19T18:58:24.963Z",
		"resource": "surveys",
		"createdBy": "1aafa574-82ce-416e-801c-588142cb4824",
		"isDeleted": false,
		"modifiedBy": "1aafa574-82ce-416e-801c-588142cb4824"
	},
	"customerId": "29e66b77-4f40-43c0-b239-1544e16cd4fc",
	"securityGroupId": "95bcaa14-10ff-4a41-90f0-5d98a960dd00"
}
```

### HTTP Request

`PATCH /surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the survey to be updated.


## Delete a survey

> Example Request

```http
DELETE /surveys/76a86650-5524-4634-bbad-ad52f5237f7d HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the survey to be deleted.

