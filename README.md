# chalk-elixir

[![Dialyxir](https://github.com/chalk-ai/chalk-elixir/actions/workflows/dialyxir.yaml/badge.svg)](https://github.com/chalk-ai/chalk-elixir/actions/workflows/dialyxir.yaml)
[![Integration tests](https://github.com/chalk-ai/chalk-elixir/actions/workflows/integration-test.yaml/badge.svg)](https://github.com/chalk-ai/chalk-elixir/actions/workflows/integration-test.yaml)
[![Publish to Hex](https://github.com/chalk-ai/chalk-elixir/actions/workflows/publish.yaml/badge.svg)](https://github.com/chalk-ai/chalk-elixir/actions/workflows/publish.yaml)

[![Hex.pm](https://img.shields.io/hexpm/v/chalk_elixir.svg)](https://hex.pm/packages/chalk_elixir)
[![Hexdocs.pm](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/chalk_elixir/)
[![Hex.pm](https://img.shields.io/hexpm/dt/chalk_elixir.svg)](https://hex.pm/packages/chalk_elixir)
[![Hex.pm](https://img.shields.io/hexpm/dw/chalk_elixir.svg)](https://hex.pm/packages/chalk_elixir)

Elixir Client for Chalk [Online Queries](https://docs.chalk.ai/docs/query-basics).


## Usage

Online queries are executed by calling "Chalk.Query.online" and passing inputs and expected outputs as descibed in the [Chalk API documentation](https://docs.chalk.ai/docs/query-basics).

```
    Chalk.Query.online(%{
        inputs: %{
            "user.id": 1
        },
        outputs: [
            "user.id"
        ]
    })
```

## Authentication

The Chalk client uses authentication credentials set in the environment variables `CHALK_CLIENT_ID` and `CHALK_CLIENT_SECRET`.  
Credentials can be generated on the Chalk dashboard or [via api](https://docs.chalk.ai/docs/online-authentication#fetching-an-access-token.

The credentials can also be passed directly when invoking the client.

```
    Chalk.Query.online(%{
        inputs: %{
            "user.id": 1
        },
        outputs: [
            "user.id"
        ]
    }, %{    
        client_id: THE_CLIENT_ID,
        client_secret: THE_SECRET
    })
```

### Supported environment variables

| Variable                                | Kind         | Description                                                                                                                                      |
| --------------------------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `CHALK_CLIENT_ID`          | **Required** | Your Chalk client ID. You must specify this environment variable or pass an explicit `client_id` value when constructing your ChalkClient         |
| `CHALK_CLIENT_SECRET`      | **Required** | Your Chalk client secret. You must specify this environment variable or pass an explicit `client_secret` value when constructing your ChalkClient |
| `CHALK_API_SERVER`         | Optional     | The API server that the client will communicate with. This defaults to https://api.chalk.ai which should be sufficient for most consumers. You can also pass an explicit `api_server` value when constructing your ChalkClient       |
| `DEPLOYMENT_ID` | Optional     | The ID of the deployment. You must specify this environment variable or pass an explicit `deployment_id` value when constructing your ChalkClient                   |

You can find relevant variables to use with your Chalk Client by
running `chalk config` with the Chalk command line tool.
