# Kraken AsyncAPI

https://www.asyncapi.com/blog/websocket-part1


% git clone git@github.com:asyncapi/cli.git
% docker build -t asyncapi/cli:latest .

## validate

% docker run --rm -it \
--user=root \
-v ./asyncapi-websocket-kraken.yml:/app/asyncapi.yml \
asyncapi/cli validate

File asyncapi.yml is valid but has (itself and/or referenced documents) governance issues.

asyncapi.yml
  1:1      warning  asyncapi-defaultContentType  AsyncAPI document should have "defaultContentType" field.
  1:1      warning  asyncapi-id                  AsyncAPI document should have "id" field.
  1:1      warning  asyncapi2-tags               AsyncAPI object should have non-empty "tags" array.
 1:11  information  asyncapi-latest-version      The latest version of AsyncAPi is not used. It is recommended update to the "3.0.0" version.  asyncapi
  3:6      warning  asyncapi-info-contact        Info object should have "contact" object.                                                     info
  3:6      warning  asyncapi-info-license        Info object should have "license" object.                                                     info

✖ 6 problems (0 errors, 5 warnings, 1 info, 0 hints)


% echo $?
0

## versions

% docker run --rm -it \
--user=root \
-v ./asyncapi-websocket-kraken.yml:/app/asyncapi.yml \
asyncapi/cli config versions
@asyncapi/cli/1.1.3 linux-arm64 node-v16.20.2
  ├@asyncapi/avro-schema-parser/3.0.5
  ├@asyncapi/bundler/0.3.11
  ├@asyncapi/converter/1.4.2
  ├@asyncapi/diff/0.4.1
  ├@asyncapi/generator/1.15.0
  ├@asyncapi/modelina/2.0.5
  ├@asyncapi/openapi-schema-parser/3.0.6
  ├@asyncapi/optimizer/0.2.3
  ├@asyncapi/parser/3.0.0-next-major-spec.14
  ├@asyncapi/protobuf-schema-parser/3.0.0
  ├@asyncapi/raml-dt-schema-parser/4.0.6
  └@asyncapi/studio/0.17.4

Repository: https://github.com/asyncapi/cli

## generate

https://www.asyncapi.com/docs/tools/generator


See generator templates list: https://www.asyncapi.com/docs/tools/generator/template

### generate @asyncapi/java-spring-template

% docker run --rm -it \
   --user=root -v ${PWD}/asyncapi-websocket-kraken.yml:/app/asyncapi.yml \
   -v ${PWD}/output:/app/output \
   asyncapi/cli generate fromTemplate -o /app/output /app/asyncapi.yml @asyncapi/java-spring-template --force-write

Lots of stuff not supported: https://github.com/asyncapi/java-spring-template

Code looks like a mess.
