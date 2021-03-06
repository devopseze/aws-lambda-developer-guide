# DeleteFunction<a name="API_DeleteFunction"></a>

Deletes the specified Lambda function code and configuration\.

If you are using the versioning feature and you don't specify a function version in your `DeleteFunction` request, AWS Lambda will delete the function, including all its versions, and any aliases pointing to the function versions\. To delete a specific function version, you must provide the function version via the `Qualifier` parameter\. For information about function versioning, see [AWS Lambda Function Versioning and Aliases](https://docs.aws.amazon.com/lambda/latest/dg/versioning-aliases.html)\. 

When you delete a function the associated resource policy is also deleted\. You will need to delete the event source mappings explicitly\.

This operation requires permission for the `lambda:DeleteFunction` action\.

## Request Syntax<a name="API_DeleteFunction_RequestSyntax"></a>

```
DELETE /2015-03-31/functions/FunctionName?Qualifier=Qualifier HTTP/1.1
```

## URI Request Parameters<a name="API_DeleteFunction_RequestParameters"></a>

The request requires the following URI parameters\.

 ** [FunctionName](#API_DeleteFunction_RequestSyntax) **   <a name="SSS-DeleteFunction-request-FunctionName"></a>
The name of the lambda function\.  

**Name formats**
+  **Function name** \- `MyFunction`\.
+  **Function ARN** \- `arn:aws:lambda:us-west-2:123456789012:function:MyFunction`\.
+  **Partial ARN** \- `123456789012:function:MyFunction`\.
The length constraint applies only to the full ARN\. If you specify only the function name, it is limited to 64 characters in length\.  
Length Constraints: Minimum length of 1\. Maximum length of 140\.  
Pattern: `(arn:(aws[a-zA-Z-]*)?:lambda:)?([a-z]{2}(-gov)?-[a-z]+-\d{1}:)?(\d{12}:)?(function:)?([a-zA-Z0-9-_]+)(:(\$LATEST|[a-zA-Z0-9-_]+))?` 

 ** [Qualifier](#API_DeleteFunction_RequestSyntax) **   <a name="SSS-DeleteFunction-request-Qualifier"></a>
Using this optional parameter you can specify a function version \(but not the `$LATEST` version\) to direct AWS Lambda to delete a specific function version\. If the function version has one or more aliases pointing to it, you will get an error because you cannot have aliases pointing to it\. You can delete any function version but not the `$LATEST`, that is, you cannot specify `$LATEST` as the value of this parameter\. The `$LATEST` version can be deleted only when you want to delete all the function versions and aliases\.  
You can only specify a function version, not an alias name, using this parameter\. You cannot delete a function version using its alias\.  
If you don't specify this parameter, AWS Lambda will delete the function, including all of its versions and aliases\.  
Length Constraints: Minimum length of 1\. Maximum length of 128\.  
Pattern: `(|[a-zA-Z0-9$_-]+)` 

## Request Body<a name="API_DeleteFunction_RequestBody"></a>

The request does not have a request body\.

## Response Syntax<a name="API_DeleteFunction_ResponseSyntax"></a>

```
HTTP/1.1 204
```

## Response Elements<a name="API_DeleteFunction_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 204 response with an empty HTTP body\.

## Errors<a name="API_DeleteFunction_Errors"></a>

 **InvalidParameterValueException**   
One of the parameters in the request is invalid\. For example, if you provided an IAM role for AWS Lambda to assume in the `CreateFunction` or the `UpdateFunctionConfiguration` API, that AWS Lambda is unable to assume you will get this exception\.  
HTTP Status Code: 400

 **ResourceConflictException**   
The resource already exists\.  
HTTP Status Code: 409

 **ResourceNotFoundException**   
The resource \(for example, a Lambda function or access policy statement\) specified in the request does not exist\.  
HTTP Status Code: 404

 **ServiceException**   
The AWS Lambda service encountered an internal error\.  
HTTP Status Code: 500

 **TooManyRequestsException**   
HTTP Status Code: 429

## See Also<a name="API_DeleteFunction_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/lambda-2015-03-31/DeleteFunction) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/lambda-2015-03-31/DeleteFunction) 