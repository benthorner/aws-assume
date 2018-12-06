# aws-assume

A script to set env vars for AWS.

## Prerequisites

You will need the following.

  * [jq](https://stedolan.github.io/jq/) to parse AWS CLI cache files
  * [aws](https://aws.amazon.com/cli/) to run AWS CLI commands

## Getting Started

Run the following to get started.

    git clone https://github.com/benthorner/aws-assume.git $HOME/.aws-assume

Then add the script to your path.

    ln -s $HOME/.aws-assume/script /usr/local/bin/aws-assume

Now make sure you have a profile.

    # ~/.aws/config
    [profile myprofile]
    role_arn = arn:aws:iam::1234567899:role/myrole
    source_profile = default
    mfa_serial = arn:aws:iam::9876543211:mfa/myaccountid

    # ~/.aws/credentials
    [default]
    aws_access_key_id = ABC123...
    aws_secret_access_key = abc123...

Check you've got AWS CLI setup.

    aws --profile myprofile sts get-caller-identity

## Running Commands

Get the env vars with just a profile.

    aws-assume <profile>

    AWS_SESSION_TOKEN=abc123...
    AWS_SECRET_ACCESS_KEY=abc123...
    AWS_ACCESS_KEY_ID=abc123...

Optionally specify a command to run.

    aws-assume <profile> 'terraform ...'
