# Set Up Your AWS S3 Environment

To begin working with AWS S3, we need to set up the environment. Here’s a step-by-step guide:

### Steps:
1. **Create an AWS Account**:
   - Go to [AWS Sign Up](https://aws.amazon.com/) and create a new account or log in to your existing account.

2. **Install AWS CLI**:
   - Download and install the AWS CLI based on your operating system:
     - [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

3. **Configure AWS CLI**:
   - After installation, open the terminal or command prompt and configure your CLI:
     ```bash
     aws configure
     ```
   - Enter your AWS Access Key, Secret Access Key, region, and output format when prompted.

4. **Set Up S3 Bucket**:
   - Go to the S3 Console at [AWS S3](https://s3.console.aws.amazon.com/s3).
   - Click **Create Bucket**, choose a unique name, select the region, and configure options like versioning or encryption.

# Basic AWS S3 Operations

In this section, we cover basic operations you can perform with AWS S3.

### 1. **Creating a Bucket**:
- Buckets are containers for storing objects (files).
  - Open the **S3 Console** and click **Create Bucket**.
  - Choose a unique name and region for your bucket.

### 2. **Uploading Files**:
- You can upload files using the console or AWS CLI.
  - To upload via the console:
    - Navigate to your bucket.
    - Click **Upload**, select the files/folders, and click **Upload** to upload.
  - To upload using AWS CLI:
    ```bash
    aws s3 cp local_file_path s3://your-bucket-name/path/
    ```

### 3. **Managing Permissions**:
- You can control who has access to your S3 bucket using **IAM Policies** and **Bucket Policies**.
- To make an object public:
  - In the **S3 Console**, select the object, click **Actions**, then choose **Make Public**.

### 4. **Deleting Objects**:
- To delete objects:
  - Select the object and click **Delete**.
  - You can also delete objects using the AWS CLI:
    ```bash
    aws s3 rm s3://your-bucket-name/path/to/object
   ```

# Hosting a Static Website on S3

In this guide, we walk through the steps of hosting a static website using AWS S3.

### Steps to Host a Static Website:

1. **Create an S3 Bucket for Website Hosting**:
   - Go to **S3 Console** and click **Create Bucket**.
   - Name the bucket to match your website domain (e.g., `www.example.com`).
   - Select the region and create the bucket.

2. **Enable Static Website Hosting**:
   - After the bucket is created, go to the **Properties** tab.
   - Scroll to **Static website hosting** and select **Use this bucket to host a website**.
   - Enter the index document (`index.html`) and error document (`error.html`).

3. **Upload Website Files**:
   - Upload your `index.html`, `error.html`, and other website assets (CSS, JS) to the S3 bucket.

4. **Set Permissions**:
   - Update the bucket policy to allow public access:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Sid": "PublicReadGetObject",
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::your-bucket-name/*"
         }
       ]
     }
     ```

5. **Test Your Website**:
   - After everything is set up, you can access your website using the S3 bucket URL (e.g., `http://your-bucket-name.s3-website-us-west-1.amazonaws.com`).
