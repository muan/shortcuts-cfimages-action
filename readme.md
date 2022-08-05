# shortcuts-cfimages-action

This repository guides you through setting up a workflow to upload an image from your Apple device to Cloudflare Images, then trigger a GitHub Action which commits the response into your repository, for you to do whatever with; for example, you can use it to [build a RSS feed for photos](https://muan.co/photos.xml). 

## Setup

Step 1: Sign up for [Cloudflare Images](https://www.cloudflare.com/products/cloudflare-images/).

Step 2: Fork this repository. Alternatively, set up a GitHub action like [`commit.yml`](.github/workflows/commit.yml) to receive the uploaded image data. But the  Shortcut in the next step assumes you are using this action.

Step 3: Setup this [ Shortcut](https://www.icloud.com/shortcuts/accdd822b5c0461eaaf24c6219ed9699) with your Cloudflare credentials and the details of your repository action.

### Cloudflare Images

Cloudflare Images is not cheap but it takes care of serving and resizing your images in the most optimal way. Alternatively, check out [muan/stories-feed-action](https://github.com/muan/stories-feed-action) which simply put images into your repository.

#### **Cloudflare API Token**

https://dash.cloudflare.com/profile/api-tokens → Create Token

#### **Cloudflare Images Account ID**

https://dash.cloudflare.com/ → Images → Developer Resources → Account ID

### `commit.yml` or a custom GitHub Action

This action takes the successful response from a Cloudflare Images upload, and appends it to a JSON file you specifiy.

###  Shortcut

This action leads you through a few steps:

- Select a photo
- Give it a caption and alt text
- Upload it to Cloudflare Images with the caption/alt as its metadata
- Trigger a `workflow_dispatch` event for a GitHub action with the response from the success upload

Triggering a `workflow_dispatch` depends on you having install the [GitHub iOS app](https://apps.apple.com/app/github/id1477376905).
