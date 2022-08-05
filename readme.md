# shortcuts-cfimages-action

This repository guides you through setting up a workflow to upload photos from your Apple device to Cloudflare Images, then trigger a GitHub Action which commits the upload response into your repository, for you to do whatever with; for example, you can use it to [build a RSS feed of photos](https://muan.co/photos.xml). 

## Setup

Step 1: Sign up for [Cloudflare Images](https://www.cloudflare.com/products/cloudflare-images/).

Step 2: Fork this repository. Alternatively, set up a GitHub Action like [`commit.yml`](.github/workflows/commit.yml) to receive the uploaded image metadata. The  Shortcut in the next step assumes you are using `commit.yml`, but it shouldn't be hard to customize.

Step 3: Install this [ Shortcut](https://www.icloud.com/shortcuts/accdd822b5c0461eaaf24c6219ed9699) and respond to setup questions with your Cloudflare credentials and the details of your GitHub Action.

### Cloudflare Images

Cloudflare Images costs $60/year, but it takes care of serving and resizing your images in the most optimal way. Alternatively, check out [muan/stories-feed-action](https://github.com/muan/stories-feed-action) which simply commits photos into your repository.

#### **Cloudflare API Token**

https://dash.cloudflare.com/profile/api-tokens → Create Token

#### **Cloudflare Images Account ID**

https://dash.cloudflare.com/ → Images → Developer Resources → Account ID

### `commit.yml` or a custom GitHub Action

This action takes the successful response from a Cloudflare Images upload, and appends it to a JSON file you specifiy.

###  Shortcut

The shortcut does the following:

- Prompt to select photo
- Prompt for caption and alt text
- Upload photo to Cloudflare Images with the caption/alt as its metadata
- Trigger a `workflow_dispatch` event for a GitHub action with the response from the success upload

The `workflow_dispatch` action depends on the [GitHub iOS app](https://apps.apple.com/app/github/id1477376905).
