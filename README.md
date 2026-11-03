RAM+ Private Server Gen
=========================

What it does
- Reads every cookie in cookies.txt (one .ROBLOSECURITY value per line).
- Reads every proxy in proxy.txt (optional - leave empty to skip proxies).
- Asks you for a Place ID.
- For each cookie, creates one VIP/private server for that place and
  appends the join link to vipserverlink.txt.
- Per-account failures (including the raw Roblox error) print to the
  console as they happen so nothing fails silently - they aren't written
  to a separate log file.

Before you run it
- cookies.txt: one raw cookie value per line, nothing else on the line.
- proxy.txt: one proxy per line, formats: host:port | host:port:user:pass
  | http://host:port. Leave it with just comments if you don't want proxies.
- The exe looks for these files in its OWN folder, so keep all 4 items
  together.

IMPORTANT - this can spend Robux
- If the target game's VIP servers are not free, Roblox will charge EACH
  account the listed price when its server is created. Double-check the
  Place ID before confirming. The app shows a summary and requires you to
  type "yes" before it creates anything.
- Test with one cookie first on a place you know the price for.

Notes / limitations
- Roblox's cookie-based VIP server creation endpoint isn't fully publicly
  documented (their docs even mark cookie auth as "not recommended"), so
  the exact request body was pieced together from Roblox's own schema
  references. If an account's attempt fails, the console line for that
  account shows the raw HTTP status and response body from Roblox - that's
  almost always enough to tell you why (expired cookie, insufficient
  Robux, VIP servers disabled for that place, invalid place ID, rate
  limiting, etc).
- A bad/expired cookie just fails that one account and moves on to the
  next; it won't stop the batch.
