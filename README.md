# iam_assume_role
Overview Diagram:
![alt text][AssumeRole0]

[Assumerole0]: https://raw.githubusercontent.com/jonskelton/iam_assume_role/master/assets/AssumeRole0.png

Download the asmrl utility: https://raw.githubusercontent.com/jonskelton/iam_assume_role/master/bin/asmrl

AWS Environment Configuration:

Profiles are supported.

~/.aws/config:
```
[default]
region=us-west-2

[profile profilename0]
output=json
```
AWS Credentials:

AWS API access credentials for the user's IAM account in the Executor AWS account.

~/.aws/credentials:
```
[default]
aws_access_key_id = AKIADEMODEMODEMO
aws_secret_key_key = sanitizedkeysanitizedkeysanitizedkey

[profilename0]
aws_access_key_id = AKIAPROFILENAME0DEMO
aws_secret_key_key = profilename0sanitizedkeysanitizedkey
```

The asmrl utility may be configured via its own configuratin file.

~/.aws/asmrl.conf:
```
{ 
  "defaults": {
    "profile": "default",
    "region": "us-west-2"
  },
  "readonly@managed0": {
    "profile": "profilename0",
    "role": "arn:aws:iam::9876543210:role/ReadOnly"
  },
  "admin@managed0": {
    "profile": "profilename0",
    "role": "arn:aws:iam::9876543210:role/Admin"
  }
}
```

Bash configuration via ~/.bashrc:
```{r, engine='bash'}
PROMPT_COMMAND='asmrl --prompt'

function readonly@managed0() {
    eval $(asmrl readonly@managed0 $1)
}

function admin@managed0() {
    eval $(asmrl admin@managed0 $1)
}
```

CLI example:
```{r, engine='bash'}
$ admin@managed0 6DIGITMFACODE
aws: admin@managed0 until 17:59:33
$ 
```
