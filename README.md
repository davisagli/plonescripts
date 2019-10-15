# Assorted Plone Scripts

This repository contains a number of maintenance scripts that have been used by Zest Software over the years while supporting Plone sites for customers.

We don't claim ownership of these, some have been written by us, some were
found in gists or elsewhere. When we know the origin of a script it's listed
below at each scripts's description and usage info. If we have missed any
attribution, please contact us at info@zestsoftware.nl

Most scripts should be started from the command line by using

> bin/instance run ./path/to/script.py --parameters

For some it also seems possible to run in a zeoclient/zeoserver setup, but
do realise that you could run into ZODB conflict errors and degraded results if the database is also written to by other zeoclients.

## purge_image_scales.py

Created by Maurits van Rees, Zest Software. This script is used to remove all images scales from objects in a plone site created by plone.scale. When you change available scales in your site, old scales will persist on the object. It is however safe to remove all of them because they will be autogenerated again.

## check_redirects.py

Created by Maurits van Rees, Zest Software. This script is used to check the automatic and manual redirects in all Plone Sites.
When called with `--fix` it will remove useless or not working redirects: redirects to content that does not exist, or redirects from a path that does exist.

## catalogoptimize.py

Created by Hanno Slichting and Helge Tesdal. This optimises the btree data structure of the portal_catalog. Over time this structure can become inbalanced, which causes longer load times
and efficiency of the catalog. We (Zest) seen noticable startup speed increases after rebalancing catalogs of larger
and longer running (4+ year) sites.

The script seems to be safe to run on an online data.fs (using subtransactions), and we havent' experienced problems with it, but please first try it on a testing environment (and test for a period afterwards).

https://raw.githubusercontent.com/hannosch/scripts/master/catalogoptimize.py

## register_intids.py

Created by Maurits van Rees, Zest Software.
Go through all content of the Plone sites, and register an intid for each item if this was not done yet.
