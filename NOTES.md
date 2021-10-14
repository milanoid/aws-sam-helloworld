# Hello world SAM application

## Yak shaving

- [AWS account](https://aws.amazon.com/console/)
- [Docker](https://www.docker.com/) (for testing app locally)
- [Homebrew](https://brew.sh/)
- [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)
- Python 3.9 ([pyenv](https://github.com/pyenv/pyenv) + [virtualenv](https://virtualenv.pypa.io/en/latest/))

Python & Pyenv
--

_Pyenv_ is a tool to install and manage multiple versions of Python interpreter.

- `pyenv install 3.9.7`
- inside project folder: `pyenv local 3.9.7` - creates `.python-version` - no need to manually switch 
- optionally `pyenv global 3.9.7`
- `which python` should return `/Users/milan/.pyenv/shims/python`

In PyCharm create a new virtual environment (virtualenv) based on pyenv interpreter 3.9.7.

SAM CLI
--
macOS's installation [instructions](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-mac.html) 

```
brew tap aws/tap
brew install aws-sam-cli
```

## SAM build, test and deploy

Hello World SAM app [guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html).

1. `sam init`
2. `sam build`
3. `sam deploy --guided`

Follow `sam init` instructions:

- AWS Quick Start Templates
- ZIP package type
- runtime Python 3.9
- Hello World Example

:gift: API Gateway endpoint (with no access restrictions!) is deployed on URL like https://83ry3sczj4.execute-api.eu-central-1.amazonaws.com/Prod/hello

```
milan@Milans-MBP-2 sam-app % http https://83ry3sczj4.execute-api.eu-central-1.amazonaws.com/Prod/hello
HTTP/1.1 200 OK
Connection: keep-alive
Content-Length: 26
Content-Type: application/json
Date: Thu, 14 Oct 2021 11:42:46 GMT
Via: 1.1 71c4b07776e0b6812900664940c9d7a7.cloudfront.net (CloudFront)
X-Amz-Cf-Id: 8pe15WRBDocUd2pBpQfYF8m_SfPj6qKgg9A1fysZb8eXS-PP5m-CrA==
X-Amz-Cf-Pop: FRA56-P4
X-Amzn-Trace-Id: Root=1-616817b5-1495787e12f6e6fc7d0b9e08;Sampled=0
X-Cache: Miss from cloudfront
x-amz-apigw-id: HMikbG5LliAFoLw=
x-amzn-RequestId: 1acfaa63-dc40-401f-95c4-0a26e7cfef13

{
    "message": "hello world"
}
```