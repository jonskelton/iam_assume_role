# iam_assume_role
Overview Diagram:
![alt text][AssumeRole0]

[Assumerole0]: https://raw.githubusercontent.com/jonskelton/iam_assume_role/master/assets/AssumeRole0.png

Download the assume-role  utility: https://raw.githubusercontent.com/jonskelton/assume-role/master/assume-role

Review documentation: https://github.com/coinbase/assume-role

Account configuration:

~/.aws/accounts
```{r, engine='json', count_lines}
{
    "executor-0": 0123456789
    "managed-0": 9876543210
}
```

Credential configuration:

~/.aws/credentials:
```
[default]
aws_access_key_id = AKIADEMODEMODEMO
aws_secret_key_key = sanitizedkeysanitizedkeysanitizedkey
```

Bash prompt via ~/.bashrc:

```{r, engine='bash', count_lines}
function aws_account_info {
  [ "$AWS_ACCOUNT_NAME" ] && [ "$AWS_ACCOUNT_ROLE" ] && echo "aws:($AWS_ACCOUNT_ROLE@$AWS_ACCOUNT_NAME) "
}
PROMPT_COMMAND='aws_account_info'
```

Bash function wrapper example:

```{r, engine='bash', count_lines}
function admin@managed-0() {
    eval $(assume-role managed-0 Admin $1)
}

$ admin@managed-0 6DIGITMFACODE
Success! IAM session envars are exported.
aws:(Admin@managed-0) 
$ 
```
