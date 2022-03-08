# Release Notes

## 0.16.0 (Jan 15, 2022)

This is the 16th release of Suzieq, with many new and useful features. Refer to the release notes for 0.16.0b1 and 0.16.0a1 for details. In addition to those features and bug fixes, this release has the following changes compared to 0.16.0b1:

* **Improved GUI Support** The new GUI had a bunch of critical bugs. This version fixes most of them. Refer to the caveats section of the GUI document for issues using it especially with the experimental feature enabled.
* **Breaking Change** Network find was broken in some cases and this has been addressed correctly. With this change, you can now get the output even if the MAC address has been aged out. This update adds a new column, l2miss, that is True if the MAC address was found in the L2 table, else false.
* You can specify a port to start the GUI on, if you can't use the default 8501.
* use-stdout for the logger is honored even if multiple poller instances are launched.
* Address table had a bug with the VRF field support thats been fixed.
* Lots more tests
* Made all the help messages associated with keywords in the CLI consistent, and clearer.

## 0.16.0 beta (Jan 7, 2022)

This release adds a bunch of major features on top of the alpha release set. 

* **New GUI**: There's a new way to sort/filter information in the GUI without having to know any pandas or fancy SQL. Check out the Xplore page for more info. One limitation with the beta release: Entire rows are not highlighted in case of a bad status, only the cell (for example only the state column in interfaces table is highlighted if down, not the entire row)
* **Snapshot Mode**: A common use case is wanting to run the SuzieQ poller in snapshot mode i.e. run once over all supported tables over all devices in the inventory, update the parquet DB and terminate. People who used this had to resort to a slightly complicated sequence of steps to achieve their goal. Now, add --run-once=update option to the sq-poller command, and you get the snapshot mode behavior. 
* Filters applied to all verbs: Before this release, you couldn't apply filters to any command except show. For example, you couldn't get summaries over interfaces with an MTU > 9200 or BGP IPv4 unicast sessions or routes populated with BGP etc. Now, a table's filters are applicable to all commands associated with that command.
* **Polling from a local folder**: If you can't run the SuzieQ poller for whatever reason, but have a directory full of show command outputs from a set of devices and want this to be used to update the Suzieq database so that you can run all your favorite suzieq commands, it is now possible with the sq-simnodes program. More details can be found on [the documentation page](https://suzieq.readthedocs.io/en/0.16.0/simnode/).
* **Improved support for IOSXE devices**: including Catalyst 4509, Catlyst 9300, Catalyst 9500 and more. 
* **QFX10K Support**: Added support for Junos QFX10K platforms. QFX10K platforms are not like QFX5K platform, they're a hybrid between QFX and MX. This is now handled correctly.
* Poller now honors use-stdout: True in the config file.
* Use hostname instead of hostnamectl for determining Cumulus and Linux hostnames (Issue #530).
* You can see the Suzieq version via suzieq-cli version OR suzieq-cli -V. Same -V option can be used for the poller, and rest server. You can get the same info via the About option from the Menu in the GUI