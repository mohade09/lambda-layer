## How to create a Lambda Layer

## https://stackoverflow.com/questions/57688731/unable-to-import-module-lambda-function-no-module-named-pandas
### *How to create a Lambda Layer*

```bash
python —version
Python 3.6.8
```
## https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html
### python 3.6 uses Amazon Linux currently
```bash
mkdir project
cd project
virtualenv v-env
source ./v-env/bin/activate
pip install pandas
deactivate
```
## creating layer
### https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html#configuration-layers-path

```bash
mkdir python
cd python

cp -r ../v-env/lib64/python3.7/site-packages/* .
zip -r s3panda_layer.zip s3panda
aws lambda publish-layer-version --layer-name s3panda --zip-file fileb://s3panda_layer.zip —compatible-runtimes python3.7
```