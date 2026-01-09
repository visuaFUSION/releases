# Release History Files

This directory contains the release history XML files that the Drupal 7 update module uses to check for available updates.

## Directory Structure

```
release-history/
  drupal/
    7.x           # Release history for Drupal 7 core
  README.md       # This file
```

## Adding a New Release

When you create a new release, update the `drupal/7.x` file by adding a new `<release>` element at the top of the `<releases>` section:

```xml
<release>
  <name>drupal 7.104</name>
  <version>7.104</version>
  <tag>7.104</tag>
  <version_major>7</version_major>
  <version_patch>104</version_patch>
  <status>published</status>
  <release_link>https://github.com/visuafusion/drupal-7/releases/tag/7.104</release_link>
  <download_link>https://github.com/visuafusion/drupal-7/archive/refs/tags/7.104.tar.gz</download_link>
  <date>UNIX_TIMESTAMP_HERE</date>
  <terms>
    <term>
      <name>Release type</name>
      <value>Security update</value>
    </term>
  </terms>
</release>
```

### Release Types

Use one of these values for the release type:
- `Security update` - For security fixes (will trigger urgent update notifications)
- `Bug fixes` - For regular bug fix releases
- `New features` - For releases with new features

### Getting Unix Timestamps

To get the current Unix timestamp:

```bash
date +%s
```

Or use an online converter like https://www.unixtimestamp.com/

## How Updates Work

1. The Drupal update module fetches this XML file from GitHub raw URLs
2. It compares the versions listed here against the installed version
3. If a newer version exists, it notifies the site administrator
4. Security updates trigger more urgent notifications

## For Contributed Modules

If you fork contributed modules for PHP 8 compatibility, create additional directories:

```
release-history/
  drupal/
    7.x
  views/
    7.x
  ctools/
    7.x
```

Each contributed module would need its own XML file following the same format.

**Note:** Contributed modules that specify their own `project status url` in their `.info` file will continue to use that URL instead of this update server.
