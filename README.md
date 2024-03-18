# Rasa-Project

Python version: 3.10
Rasa version: 3.6.19

Install Python Dependency:
	pip install rasa

Install nginx : web-server using here for proxy pass

	Add below line of code in nginx.conf file under the server block (nginx.conf can be found in repo for your reference):
	
		location /webhook/001 {
			proxy_pass http://127.0.0.1:5057/webhooks/rest/webhook/;
		}
		location /webhook/002 {
			proxy_pass http://127.0.0.1:5056/webhooks/rest/webhook/;
		}

Pull the repo:
	
	Run both Model:
	
		run the below command under this directory: Rasa-Bot-001 (Bot 001 is going to run in port 5057 we are explictly defining with -p)
			rasa run -p 5057
			
		run the below command under this directory: Rasa-Bot-002 Bot 002 is going to run in port 5056 we are explictly defining with -p)
			rasa run -p 5056
		
Install postman: to check bot status and response
		Post method use the url : localhost/webhook/001
		In the body raw data paste below block:
			{
				"sender": "postman",
				"message": "hi"
			}
	
