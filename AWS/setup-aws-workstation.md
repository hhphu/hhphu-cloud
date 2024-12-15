# Set up AWS workstation

## Add Profile to local machine
- To set up profile on our local machine, `Access Key ID` & `Secret Access Key` are needed.
- Run `aws configure --profile $PROFILE_NAME` with the default output format as `json`

## Install aws-vault
- Download the Binary file (this is for my Ubuntu machine). 
```bash
curl -o aws-vault https://github.com/99designs/aws-vault/releases/download/v6.3.0/aws-vault-linux-amd64
```
- Move the binary to a directory to our path: `sudo mv aws-vault /usr/local/bin/`

- Set permissions `sudo chmod +x /usr/local/bin/aws-vault`

- Verify the installation `aws-vault --version`

  ## Set up profile in aws-vault
  - Add a profile to aws-vault: `aws-vault add $PROFILE_NAME
 
  ## Create policy for the profile
  Go to AWS console and attach the following to the above user:
  ```bash
  {
     "Version": "2012-10-17",
     "Statement": [
      {
       "Effect": "Allow",
       "Action": "iam:GetUser",
       "Resource": "arn:aws:iam::715774824824:user/$PROFILE_NAME"
      },
      {
       "Effect": "Allow",
       "Action": "sts:GetFederationToken",
       "Resource": "arn:aws:sts::715774824824:federated-user/*"
      }
     ]
  }
```
This allows aws-vault to log the user in from the terminal.

## Testing the setup
- Open a browser window and login to the AWS console
```bash
aws-vault login $PROFILE_NAME
```
- Execute a command (using temporary credentials)
```bash
aws-vault exec $PROFILE_NAME -- aws s3 ls
```

- Starting a subshell
```bash
aws-vault exec $PROFILE_NAME
```
