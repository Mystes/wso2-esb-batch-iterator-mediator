# WSO2 ESB Batch Iterator Mediator
![Build status](https://circleci.com/gh/Mystes/wso2-esb-batch-iterator-mediator.svg?style=shield&circle-token=df6d6b6f67a9bdc7f7d58667942a6dcfeb7e0f62)

## What is WSO2 ESB?
[WSO2 ESB](http://wso2.com/products/enterprise-service-bus/) is an open source Enterprise Service Bus that enables interoperability among various heterogeneous systems and business applications.

## Features
Batch Iterator Mediator extends [WOS2 Iterate Mediator](https://docs.wso2.com/display/ESB500/Iterate+Mediator) by providing iteration by several elements (batch) at a time.

## Usage

### 1. Get the WSO2 ESB Bacth Iterator Mediator jar

You have two options:

a) Add as a Maven/Gradle/Ivy dependency to your project. Get the dependency snippet from [here](https://bintray.com/mystes/maven/wso2-esb-batch-iterator-mediator/view).

b) Download it manually from [here](https://github.com/Mystes/wso2-esb-batch-iterator-mediator/releases).

### 2. Install the mediator to the ESB
Copy the `wso2-esb-batch-iterator-mediator-x.y.jar` to `$WSO2_ESB_HOME/repository/components/dropins/`.

### 3. Use it in your proxies/sequences
Mediator can be used as follows:
```xml
<batchIterator batchSize="number" [continueParent=(true | false)] [preservePayload=(true | false)] (attachPath="xpath")? expression="xpath">
   <target [to="uri"] [soapAction="qname"] [sequence="sequence_ref"] [endpoint="endpoint_ref"]>
     <sequence>
       (mediator)+
     </sequence>?
     <endpoint>
       endpoint
     </endpoint>?
   </target>+
</batchIterator>
```

#### Example
```xml
<batchIterator batchSize="3" expression="//iterate">
   <target>
     <sequence>
       <!-- Do something here with elements -->
     </sequence>
   </target>
</batchIterator>
```

## Technical Requirements

#### Usage

* Oracle Java 6 or above
* WSO2 ESB
    * Wrapper Mediator has been tested with WSO2 ESB versions 4.9.0 & 5.0.0

#### Development

* Java 6 + Maven 3.0.X

### Contributors

- [Kreshnik Gunga](https://github.com/kgunga)
- [Ville Harvala](https://github.com/vharvala)

## [License](LICENSE)

Copyright &copy; 2016 [Mystes Oy](http://www.mystes.fi). Licensed under the [Apache 2.0 License](LICENSE).
