# Create DynamoDB

![image](https://github.com/hhphu/Cloud/assets/45286750/f88777a0-bb88-4adf-8c04-a3f42af41aa3)

# INTRODUCTION
- This post will go through all steps to create a DynamoDB to store the number of visits everytime a user lands on the website

# CREATE TABLE
To create a table:
- Go to **DynamoDB** > **Table** > **Create Table**
- Table name: hhphu.click-count
- Partrition key: id and set it to Number
- **Create table**
 
    ![image](https://github.com/hhphu/Cloud/assets/45286750/04f3f46b-2c1f-45b2-8533-9fbefb951c2f)

**Initialize the key id's value**
- Select the databse & click **Actions** > **Create item**.
    - Enter value 1 for the key **_id_**
    - Add an attribute **views** with value 1
    - **Create item**
 
Once completed, we can click **Explore table** to verify the data

![image](https://github.com/hhphu/Cloud/assets/45286750/36b64ec7-0f38-4565-bc45-2bd5e61cfc90)

# CREATE LAMBDA FUNCTION
Go to the **AWS Lambda** service and create a new lambda function with the following options:
- Function name: hhphu-click-get-count
- Runtime: Python 3.12
- IN **Advanced settings** sectopm. check the box **Enable function URL**. This provides and endpoint for users to access the function
- Auth type: NONE. This means that anyone from the public can access and execute the function without having to provide authentication.
- Check the box: COnfigure cross-origin resource sharing (CORS): white list the sources from which the Lambda function can be fetched.

![image](https://github.com/hhphu/Cloud/assets/45286750/6d4db573-d743-495e-939d-3faa0b01f53a)

From the screenshot above, click the function URL and we should see the message from the default function.

![image](https://github.com/hhphu/Cloud/assets/45286750/8b37da92-f9d9-4638-9ab7-c83d19b89719)

## Edit Lambda code
Now we have to update the Lambda function to retrieve the count and update it

```python
import json
import boto3

dynamodb = boto3.resource('dynamodb')                # Request AWS DynamoDB
table = dynamodb.Table('hhphu.click-count')          # Retrieve the table name hhphu.click-count

def lambda_handler(event, context):
    response = table.get_item(Key={'id': 1})          # Retrive the item whose id=1
    views = response["Item"]["views"]                 # Extract the "views" attribute from the response
    views +=1
    
    response = table.put_item(Item={                  # Update the value of "views" in the table
        'id': 1,
        'views': views 
    })
    # TODO implement
    return (views)

```


