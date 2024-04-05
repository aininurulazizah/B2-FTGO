#FROM python:2.7.16-alpine3.9
FROM python:3.9-alpine3.14
RUN pip install awscli --upgrade --index-url https://pypi.org/simple/
RUN pip install pyyaml --upgrade --index-url https://pypi.org/simple/
COPY create-dynamodb-tables.sh .
COPY ftgo-order-history.json .
COPY wait-for-dynamodblocal.sh .
RUN chmod +x *.sh
HEALTHCHECK --interval=10s --retries=10 --timeout=3s CMD [[ -f /tables-created ]]

CMD ./wait-for-dynamodblocal.sh && ./create-dynamodb-tables.sh
