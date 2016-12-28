# Language detection API

This repository contains a dockerized version of [Elasticsearch](https://github.com/docker-library/elasticsearch) with the [https://github.com/jprante/elasticsearch-langdetect](Language Detect plugin). **The goal is to have a language detection API up and working within a 2 minutes. The precision is over 99% for 53 languages.**

To run it:
```
docker run --name language-detection-api --rm -p 9200:9200 antoinefinkelstein/elasticsearch-langdetect
```

**You're ready to use it!** For example:
```
curl -XPOST 'localhost:9200/_langdetect?pretty' -d 'This is a test'
{
  "profile" : "/langdetect/",
  "languages" : [ {
    "language" : "en",
    "probability" : 0.9999972283490304
  } ]
}
curl -XPOST 'localhost:9200/_langdetect?pretty' -d 'Das ist ein Test'
{
  "profile" : "/langdetect/",
  "languages" : [ {
    "language" : "de",
    "probability" : 0.9999985460514316
  } ]
}
curl -XPOST 'localhost:9200/_langdetect?pretty' -d 'Datt isse ne test'
{
  "profile" : "/langdetect/",
  "languages" : [ {
    "language" : "no",
    "probability" : 0.5714275763833249
  }, {
    "language" : "nl",
    "probability" : 0.28571402563882925
  }, {
    "language" : "de",
    "probability" : 0.14285660343967294
  } ]
}
```

## License

Elasticsearch Langdetect Plugin

Derived work of language-detection by Nakatani Shuyo http://code.google.com/p/language-detection/

Copyright (C) 2012 Jörg Prante

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. you may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
