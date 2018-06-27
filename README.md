# Kubernetes Blue/Green @EKS

![Build Status](https://codebuild.us-west-2.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiOWV1anl4VXc2SlZyekUyNDk1TjZSdDVjenNDUVhMV21lU0xocE5ERVpxRGp3cjc3dmdsQ1R4SE1qUXg0a0gzSFdhNzNFUzJvT3N4UVVSc0dXV0k4ekhFPSIsIml2UGFyYW1ldGVyU3BlYyI6InJDNzVFWjhVVXRFWkRLTHIiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)

EKSで Blue/Green Deployment をやってみよう。

## やること

CodePipelineを使って以下の流れを実行する。  
CommitのたびにBlue/Green Deploymentされます。

1. git push
2. CodeBuildでDockerイメージをビルド
3. ECRにイメージをpush & Kubernetes YAMLをS3にpush
4. AWS Lambdaをキックして新しいDeploymentをデプロイ
5. Serviceの向け先を新旧のDeploymentで入れ替える
6. 古いDeploymentを削除
