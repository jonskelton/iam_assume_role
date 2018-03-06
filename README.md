# iam_assume_role
Overview Diagram:
![alt text][AssumeRole0]

[Assumerole0]: https://raw.githubusercontent.com/jonskelton/iam_assume_role/master/assets/AssumeRole0.png

Download the assume-role  utility: https://raw.githubusercontent.com/jonskelton/assume-role/master/assume-role

Review documentation: https://github.berkeley.edu/ist-api-eis/coinbase_assume-role

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
function example-role-name@example-account-alias() {
    eval $(assume-role example-account-alias example-role-name $1)
}

$ example-role-name@example-account-alias 6DIGITMFACODE
Success! IAM session envars are exported.
aws:(example-role-name@example-account-alias) 
$ 
```
