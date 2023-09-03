## Apache Iceberg Event Based Compaction of Small Files in Amazon EMR

Apache Iceberg tables store metadata of the data in manifest files. As the number of data files increase, the amount of metadata stored in these manifest files also increases, leading to longer query planning time. The query execution time also increases as it is proportional to the number of data/metadata file read operations. Compaction is the process of combining these small data/metadata files to improve performance and reduce cost.

To compact the small files for improved performance, in this example, Amazon EMR will trigger a compaction job after the write commit as a post commit hook when defined thresholds (e.g. number of commits) are met. By default, Amazon EMR will wait for 10 commits to trigger the post-commit hook compaction utility.

In this example notebook we are going to show you how the Compaction utility can be used and what performance benefits you can achieve by using this utility. We will be using an EMR Notebook for demonstrating the benefits of the compaction utility. To check how to setup an EMR Notbook, please refer to our AWS documentations. ![image](https://github.com/aws-samples/emr-iceberg-small-file-optimization/assets/38989589/4c904ef9-4e22-4204-b462-47a618a35480)

## Prerequisite
For running the Amazon EMR tests in this example, You have to use Amazon EMR version emr-6.11.0 or higher with Spark 3.3.2, and JupyterEnterpriseGateway 2.6.0. The cluster we used was having 1 Primary Node (r5.2xlarge) and 2 Core Nodes(r5.xlarge). We used a bootstrap action during cluster creation to enable event-based table management as below.

sudo aws s3 cp s3://<path>/iceberg-aws-event-based-table-management-0.1.jar /usr/lib/spark/jars/

Also, you should check our documentation on how to use an Iceberg cluster with Spark which is a prerequisite for this exercise. To leverage the feature, you have to use the iceberg-aws-event-based-table-management source code (https://github.com/aws-samples/iceberg-aws-event-based-table-management/tree/main/src/main/java/org/apache/iceberg/aws/manage) and provide the built jar in the engine’s class-path. 


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

