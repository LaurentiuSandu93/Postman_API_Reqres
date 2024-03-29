# Postman-API

### {
	"info": {
		"_postman_id": "fa0abe28-fe1e-41ce-b287-5acc537695b2",
		"name": "Reqres API",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "32904685"
	},
	"item": [
		{
			"name": "get List Users",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 200', function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							"pm.test('Verify if Response time is less than 400ms', function () {\r",
							"    pm.expect(pm.response.responseTime).to.be.below(400);\r",
							"});\r",
							"\r",
							"var data= pm.response.json();\r",
							"pm.test(\"Verify if the results for the first user are correct\", function () {\r",
							"    pm.expect(data[0].id).to.eql(1);\r",
							"    pm.expect(data[0].email).to.eql(\"george.bluth@reqres.in\");\r",
							"    pm.expect(data[0].first_name).to.eql(\"George\");\r",
							"    pm.expect(data[0].last_name).to.eql(\"Bluth\");\r",
							"    pm.expect(data[0].avatar).to.eql(\"https://reqres.in/img/faces/1-image.jpg\");\r",
							"    console.log(data[0].id);\r",
							"    console.log(data[0].email);  \r",
							"    console.log(data[0].first_name);  \r",
							"    console.log(data[0].last_name);  \r",
							"    console.log(data[0].avatar);  \r",
							"});\r",
							"\r",
							"// Verificam ca raspunsul contine campul id\r",
							"pm.test(\"Response contains ID\", function () {\r",
							"   pm.expect(pm.response.text()).to.include(\"id\");});\r",
							"\r",
							"   // Verificam ca raspunsul returneaza exact sase carti\r",
							"var data = pm.response.json();\r",
							"pm.test('Number of books = ' + data.length, function () { // functia length nu poate fi folosita decat pentru liste\r",
							"pm.expect(data.length).to.equal(12);});\r",
							"\r",
							"//Verificam performanta requestului\r",
							"pm.test(\"Response time is less than 5s\", () => {\r",
							"pm.expect(pm.response.responseTime).to.be.below(5000);});\r",
							"\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/users?page=1",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"users"
					],
					"query": [
						{
							"key": "page",
							"value": "1"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "get single user",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 200', function () {\r",
							"    pm.response.to.have.status(200);\r",
							"})\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/users/2",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"users",
						"2"
					]
				}
			},
			"response": []
		},
		{
			"name": "get single user 404 error",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 404', function () {\r",
							"    pm.response.to.have.status(404);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "https://reqres.in/api/users/23",
					"protocol": "https",
					"host": [
						"reqres",
						"in"
					],
					"path": [
						"api",
						"users",
						"23"
					]
				}
			},
			"response": []
		},
		{
			"name": "get list <resource>",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 200', function () {\r",
							"    pm.response.to.have.status(200);\r",
							"})\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{url}}/api/unknown",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"unknown"
					]
				}
			},
			"response": []
		},
		{
			"name": "get single resource",
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{url}}/api/unknown/4",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"unknown",
						"4"
					]
				}
			},
			"response": []
		},
		{
			"name": "get single resource 404 error",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 404', function () {\r",
							"    pm.response.to.have.status(404);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "https://reqres.in/api/unknown/23",
					"protocol": "https",
					"host": [
						"reqres",
						"in"
					],
					"path": [
						"api",
						"unknown",
						"23"
					]
				}
			},
			"response": []
		},
		{
			"name": "post create user",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"name\": \"laurentiu\",\r\n    \"job\": \"QA manual tester\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/users2",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"users2"
					]
				}
			},
			"response": []
		},
		{
			"name": "post register",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"email\": \"eve.holt@reqres.in\",\r\n    \"password\": \"pistol\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/register",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"register"
					]
				}
			},
			"response": []
		},
		{
			"name": "post register 404 error",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 400', function () {\r",
							"    pm.response.to.have.status(400);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"email\": \"sydney@fife\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://reqres.in/api/register",
					"protocol": "https",
					"host": [
						"reqres",
						"in"
					],
					"path": [
						"api",
						"register"
					]
				}
			},
			"response": []
		},
		{
			"name": "post login successful",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"email\": \"eve.holt@reqres.in\",\r\n    \"password\": \"cityslicka\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/login",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"login"
					]
				}
			},
			"response": []
		},
		{
			"name": "post unsuccessful login",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"// test 1: verifica faptul ca status code-ul este cel corect \r",
							"pm.test(\"Check that the status code of the request is the correct one\",() =>{\r",
							"   pm.response.to.have.status(400)})\r",
							"\r",
							"pm.test(\"Response returns error\", function () {\r",
							"   pm.expect(pm.response.text()).to.include(\"error\");\r",
							"});\r",
							"\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"email\": \"peter@klaven\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://reqres.in/api/login",
					"protocol": "https",
					"host": [
						"reqres",
						"in"
					],
					"path": [
						"api",
						"login"
					]
				}
			},
			"response": []
		},
		{
			"name": "put update",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test('Verify if Status code is 200', function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "PUT",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"name\": \"laurentiu sandu\",\r\n    \"job\": \"qa manual tester\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/users/2",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"users",
						"2"
					]
				}
			},
			"response": []
		},
		{
			"name": "patch update",
			"request": {
				"method": "PATCH",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"name\": \"laur93\",\r\n    \"job\": \"QA team leader\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{url}}/api/users/2",
					"host": [
						"{{url}}"
					],
					"path": [
						"api",
						"users",
						"2"
					]
				}
			},
			"response": []
		},
		{
			"name": "delete user",
			"request": {
				"method": "DELETE",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://reqres.in/api/users/2",
					"protocol": "https",
					"host": [
						"reqres",
						"in"
					],
					"path": [
						"api",
						"users",
						"2"
					]
				}
			},
			"response": []
		},
		{
			"name": "New Request",
			"request": {
				"method": "GET",
				"header": []
			},
			"response": []
		}
	]
}
