# Remove the engineering alpha and restore security

Do this when testing ends. Export your support ZIP first. These steps do not
delete captures, app reports or other drivers.

1. Finish capture/verification, stop tape motion, quit rewindDV, stop extended
   logging (Control-C), and disconnect FireWire.
2. **Uninstall the driver before deleting its containing app.** With SIP still
   disabled, inspect the installed extension:

   ```sh
   systemextensionsctl list | grep -F 'net.rewinddigital.RewindDV.Driver'
   ```

   This package uses the ad-hoc team identifier `-`. If a different identity
   appears, stop and contact support; do not substitute another vendor or team.
   If no entry is present, skip the uninstall command. Otherwise run:

   ```sh
   sudo systemextensionsctl uninstall - net.rewinddigital.RewindDV.Driver
   ```

   Restart if requested or if marked `terminated waiting for uninstall on reboot`.
   Check the list again. No output means no registered rewindDV extension was
   listed. **Never run
   `systemextensionsctl reset`**, never delete `/Library/SystemExtensions`
   manually, and never remove another vendor's driver.
3. After the extension is absent, move **/Applications/rewindDV.app** to Trash
   using Finder. Deleting the app alone is not proof its driver was removed.
4. Disable the development setting in normal macOS:

   ```sh
   sudo systemextensionsctl developer off
   ```

5. Shut down. Hold power until startup options appear. **Options → Continue →
   Utilities → Terminal**, then run:

   ```sh
   csrutil enable
   ```

   Restart normally. If you separately changed Startup Security policy while
   troubleshooting, restore your original policy (normally Full Security) using
   Startup Security Utility. This package did not instruct any AMFI, boot-argument
   or global Gatekeeper changes.
6. Verify:

   ```sh
   csrutil status
   systemextensionsctl list | grep -F 'net.rewinddigital.RewindDV.Driver'
   test ! -e '/Applications/rewindDV.app' && echo 'rewindDV app removed'
   ```

   Expect SIP `enabled`, no rewindDV extension entry, and `rewindDV app removed`.
   Do not resume testing with the ad-hoc driver after restoring SIP.

## If the Mac cannot start normally

Disconnect FireWire, then try Safe Mode: shut down, hold power to startup options,
select the startup disk, hold Shift and choose Continue in Safe Mode. Remove only
rewindDV as above. Do not
experiment with boot arguments or erase anything. Keep your backups available.

## Retained data

Capture folders remain wherever you selected them. App evidence is inside:
`~/Library/Containers/net.rewinddigital.RewindDV/Data/Library/Application Support/RewindDV/`

Optional extended logs are inside:
`~/Library/Application Support/rewindDV Alpha/SystemLogs/`

After preserving needed evidence, these specific rewindDV-only folders and
Desktop support ZIPs may be moved to Trash manually. Do not delete the Library,
Containers, Application Support or Desktop parent directories.
