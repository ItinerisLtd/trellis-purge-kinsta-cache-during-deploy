# trellis-purge-kinsta-cache-during-deploy

[![GitHub tag](https://img.shields.io/github/tag/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy.svg)](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy/tags)
[![license](https://img.shields.io/github/license/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy.svg)](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy/blob/master/LICENSE)


Purge [Kinsta](https://bit.ly/2NWj3sg) cache when [Trellis](https://github.com/roots/trellis) deploys [Bedrock](https://github.com/roots/bedrock).

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Requirements](#requirements)
- [Installation](#installation)
- [Role Variables](#role-variables)
- [Usage](#usage)
- [FAQs](#faqs)
  - [What is `kinsta_purge_cache_endpoint`?](#what-is-kinsta_purge_cache_endpoint)
  - [Where can I find my `kinsta_purge_cache_endpoint`?](#where-can-i-find-my-kinsta_purge_cache_endpoint)
- [See Also](#see-also)
- [Testing](#testing)
  - [Syntax Check](#syntax-check)
- [Author Information](#author-information)
- [Feedback](#feedback)
- [Change log](#change-log)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Requirements

- Trellis [411981f](https://github.com/roots/trellis/commit/411981fb4a7ef9be079f50fbf317db9fc290e91b) or later
- Ansible v2.6 or later
- [Kinsta](https://bit.ly/2n1okDu) account with SSH access

## Installation

Add this role to `requirements.yml`:
```yaml
# requirements.yml
- src: https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy
  version: 0.1.0 # Check for latest version!
```

Run the command:
```bash
➜ ansible-galaxy install -r requirements.yml --force
```

## Role Variables

Add this role to the [`deploy_after` hook](https://roots.io/trellis/docs/deploys/#hooks):
```yaml
# group_vars/all/deploy-hooks.yml
# Learn more on https://roots.io/trellis/docs/deploys/#hooks
deploy_after:
  - "{{ playbook_dir }}/vendor/roles/trellis-purge-kinsta-cache-during-deploy/tasks/main.yml"
```

Define `kinsta_purge_cache_endpoint` in `group_vars/<env>/kinsta.yml`:
```yaml
# group_vars/<env>/kinsta.yml
# Ask Kinsta support for the URL to clearing the cache on your site
# Use full URL, i.e: starts with `https://`
kinsta_purge_cache_endpoint: 'https://aaa.com/bbb/ccc?ddd=eee'
```

## Usage

[Deploy](https://roots.io/trellis/docs/deploys/#example) as usual. No special action needed.

## FAQs

### What is `kinsta_purge_cache_endpoint`?

The URL to trigger Kinsta cache purging, same as clicking the purge button on web UI. Each environment(production, staging, etc) has its own unique `kinsta_purge_cache_endpoint`.

### Where can I find my `kinsta_purge_cache_endpoint`?

Ask Kinsta support.

## See Also

- [How to Use Bedrock and Trellis at Kinsta (WordPress Development)](https://bit.ly/2v8FW50)

## Testing

### Syntax Check

```bash
➜ ansible-playbook -i 'localhost,' --syntax-check tests/test.yml
```

## Author Information

[trellis-purge-kinsta-cache-during-deploy](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy) is a [Itineris Limited](https://www.itineris.co.uk/) project created by [Tang Rufus](https://typist.tech).

Special thanks to [the Roots team](https://roots.io/about/) whose [Trellis](https://github.com/roots/trellis) make this project possible.

Full list of contributors can be found [here](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy/graphs/contributors).

## Feedback

**Please provide feedback!** We want to make this library useful in as many projects as possible.
Please submit an [issue](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy/issues/new) and point out what you do and don't like, or fork the project and make suggestions.
**No issue is too small.**

## Change log

Please see [CHANGELOG](./CHANGELOG.md) for more information on what has changed recently.

## License

[trellis-purge-kinsta-cache-during-deploy](https://github.com/ItinerisLtd/trellis-purge-kinsta-cache-during-deploy) is released under the [MIT License](https://opensource.org/licenses/MIT).
