# action-github-app-token

This uses GitHub Apps to fetch a GitHub auth token for a GitHub App installation.
The GitHub App is used to authorize API access across multiple repositories.

## Development

Install the dependencies
```bash
$ yarn
```

Build the typescript and package it for distribution
```bash
$ yarn build
```

## Usage

You'll want to fork this and use your own GitHub Application's ID and add an organization secret with the App's private key.

The action will then provide a `token` output.

```
  - name: my-app-install token
    id: my-app
    uses: 'getsentry/action-github-app-token'
    with:
      private_key: ${{ secrets.APP_PRIVATE_KEY }}

  - name: Checkout private repo
    uses: actions/checkout@v2
    with:
      repository: getsentry/my-private-repo
      token: ${{ steps.my-app.output.token }}
```
