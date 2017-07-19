# Test

[Rusoto](https://github.com/rusoto/rusoto "Rusoto") is an AWS SDK for Rust.

Rusoto consists of one [core](https://github.com/rusoto/rusoto/tree/master/rusoto/core "Rusoto Core") crate, containing common functionality  
shared across services, and then a crate for [each supported service](supported-aws-services.md).

Services are generated from the [botocore](https://github.com/boto/botocore "Botocore") project's API definitions.

In addition to the main crates, Rusoto also provides a [credential](https://github.com/rusoto/rusoto/tree/master/credential "Rusoto credential")  
and a [helpers](https://github.com/rusoto/rusoto/tree/master/helpers "Rusoto helpers") crate. The credential crate provides the necessary  
functionality for properly loading and handling AWS credentials. The helpers  
crate provides higher-level abstractions for some of the AWS services \(e.g. S3\),  
however further development of the crate has been put on hold until the two main  
crates have reached a stable state.

{% youtube src="https://www.youtube.com/watch?v=9bZkp7q19f0" %}{% endyoutube %}



