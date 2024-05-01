# CableStore

[![CircleCI](https://circleci.com/gh/buhrmi/cablestore.svg?style=shield)](https://circleci.com/gh/buhrmi/cablestore)
[![Gem Version](https://badge.fury.io/rb/cablestore.svg)](https://rubygems.org/gems/cablestore)
[![npm version](https://badge.fury.io/js/@buhrmi%2Fcablestore.svg)](https://www.npmjs.com/package/@buhrmi/cablestore)

CableStore gives you Svelte stores that connect to your 
Rails application via ActionCable and can be manipulated
via your server-side application code.

> **Note**
> It's still early, and there's currently no way to configure the Websocket URL (it uses the Rails default `/cable`).

## Installation

### Ruby gem

Add this line to your application's Gemfile:

```ruby
gem 'cablestore'
```

And then execute:

    $ bundle install

### Npm package

Install the package:

    $ yarn add @buhrmi/cablestore

## Usage

### Subscribe to an ActiveRecord object

To subscribe to ActiveRecord object, you have to pass the signed Global ID to the frontend. For example, via a controller action:

```rb
def show
  @sgid = User.to_signed_global_id(expires_in: nil).to_s
end
```

Then you can subscribe to it in your client-side code:

```js
import { subscribe } from '@buhrmi/cablestore'

const store = subscribe(sgid, nil, 'current_user')
```
