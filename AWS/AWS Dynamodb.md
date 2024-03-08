---

---
Links: [[Projeto AWS]], [[Conceitos Base]]
___
ideia:  meter a db pulbica mas os acessos bons com senha
# Python 
Para começar temos de criar temos de dar `import boto3`, e criar um recurso da instância DynamoDB e dar o nome da tabela. Isto usa a conta default
```
# Creation of the DynamoDB resource

aws_region = 'eu-west-1'

dynamodb = boto3.resource('dynamodb', region_name=aws_region, aws_access_key_id="AKIATJJZWPFTYLQJYIW6",   aws_secret_access_key="b4vdkQNIyAis7dkjUwF88FsHJXxnOb9r6042Ry9Z")

  

# Create a DynamoDB table object

table = dynamodb.Table('cloud-resume-challenge')
```

*A função a ser chamada está  no ficheiro YAML*
## Função GET
Acho que isto está mal feito por causa de como está a tabela na db

| ID       	| Visitors 	|
|----------	|----------	|
| Visitors 	| Num      |
```
def lambda_handler(event, context):

  

    # Retrieve item from DynamoDB table and putting it as float

    try:

        response_body = table.get_item(Key={"ID": "visitors"})["Item"]["visitors"]

        visitor_count_float = int(response_body)

        # Create the HTTP response with CORS headers

        response = {

            "statusCode": 200,

            "headers": {

                "Access-Control-Allow-Origin": "*",  # Adjust the origin as needed

                "Access-Control-Allow-Headers": "*",

                "Access-Control-Allow-Methods": "*"

            },

            "body": json.dumps({"visitor_count": visitor_count_float})  # Convert dictionary to JSON string

        }

    except Exception as e:

        # Handle exceptions

        response = {

            "statusCode": 500,

            "headers": {

                "Access-Control-Allow-Origin": "*",  # Adjust the origin as needed

                "Access-Control-Allow-Headers": "*",

                "Access-Control-Allow-Methods": "*"

            },

            "body": json.dumps({"error_message": str(e)})

        }
```

## Função Update 
|ID|Visitors|
|---|---|
|Visitors|Num|