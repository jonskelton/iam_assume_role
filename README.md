# iam_assume_role
Overview Diagram:
![alt text][AssumeRole0]

[Assumerole0]: https://raw.githubusercontent.com/jonskelton/iam_assume_role/master/assets/AssumeRole0.png

Download the assume-role  utility: https://raw.githubusercontent.com/jonskelton/assume-role/master/assume-role

Review documentation: https://github.berkeley.edu/ist-api-eis/coinbase_assume-role

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
