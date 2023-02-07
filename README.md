# benthos-1731

Run the following a few times and also try to change the order of files in the
command:

```sh
benthos streams \
  config.proxy.yml \
  config.accounts.yml \
  config.oauth.yml \
  config.uploads.yml
```

Expect to see output like this:

```
INFO Running without a main config file            @service=benthos
ERRO Failed to connect to inproc output 'handle_account_rpc': pipe was not found  @service=benthos label="" path=root.input stream=config.accounts
ERRO Failed to connect to inproc output 'handle_oauth_rpc': pipe was not found  @service=benthos label="" path=root.input stream=config.oauth
ERRO Failed to connect to inproc output 'handle_upload_rpc': pipe was not found  @service=benthos label="" path=root.input stream=config.uploads
INFO Receiving HTTP messages at: http://localhost:3000/  @service=benthos label=proxy path=root.input stream=config.proxy
INFO Sending inproc messages to ID: handle_oauth_rpc  @service=benthos label=proxy_oauth_rpc path=root.output.switch.0.output stream=config.proxy
INFO Sending inproc messages to ID: handle_account_rpc  @service=benthos label=proxy_account_rpc path=root.output.switch.1.output stream=config.proxy
INFO Launching benthos in streams mode, use CTRL+C to close  @service=benthos
INFO Sending inproc messages to ID: handle_upload_rpc  @service=benthos label=proxy_upload_rpc path=root.output.switch.2.output stream=config.proxy
INFO Listening for HTTP requests at: http://0.0.0.0:4195  @service=benthos
INFO Receiving inproc messages from ID: handle_oauth_rpc  @service=benthos label="" path=root.input stream=config.oauth
INFO Receiving inproc messages from ID: handle_account_rpc  @service=benthos label="" path=root.input stream=config.accounts
INFO Receiving inproc messages from ID: handle_upload_rpc  @service=benthos label="" path=root.input stream=config.uploads
```
