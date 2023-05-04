# i3status blocks to monitor astro campaign

Those scripts have been written for use in [i3status-rust][i3status-rust] with custom blocks:

```
[[block]]
block = "custom"
command = "astrodelivery"
on_click = "<command>"
interval = 1800
json = true
```

Such a block will update every 30 minutes (or when you click on it), and display
a "critical" status (colors will depend on your theme) when your delivery status
changes to "locked" (or, for `astroupdates`, when new update is published).

You'll have to put `astrodelivery` and/or `astroupdates` scripts somewhere that
is in your path (I use `~/bin/` for example) and edit them to point to your
configuration file.

## Configuration file

* `last_update` field is the **number** of updates published so far
* `campaign_id` is the astro slide campaign id, no need to update it unless you
  want to monitor a different igg campaign (same for `campaign_slug`)
* `user_id` is your igg user id, which you can retrieve from the url of your
  profile (`123456` in `https://www.indiegogo.com/individuals/123456`)
* `contrib_id` is the id of the contribution you want to track. Head to "my
  contributions", click on "view details" and extract your contribution id from
  the url (`https://www.indiegogo.com/individuals/[user_id]/contributions/123456`)
* `cookie` is your cookie string for igg website; you can get it from your browser
  devtools (**DO NOT SHARE THAT WITH ANYONE**)

[i3status-rust]: https://github.com/greshake/i3status-rust
