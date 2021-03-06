# Supybot

Example:

    docker run -d --name mysupybot \
               -e SUPYBOT_CHANNELS="#mychannel" \
               -e SUPYBOT_IDENT=mysupybot \
               -e SUPYBOT_NETWORK=freenode \
               -e SUPYBOT_NICK=mysupybot \
               -e SUPYBOT_PORT=6697 \
               -e SUPYBOT_PREFIXES='@&' \
               -e SUPYBOT_PREFIX_STRINGS="HEY" \
               -e SUPYBOT_SERVER=irc.freenode.net \
               -e SUPYBOT_USER=bot \
               -e SUPYBOT_USE_SSL=True \
               -e SUPYBOT_OWNER=supyadmin \
               -e SUPYBOT_OWNER_PASS=adminpass \
               obosob/supybot

This will build an initial config and start supybot in a detached container
called "supybot".  Further configuration can be done from a query window
with your bot in your IRC client.

If you already have a configuration situated at /var/lib/mysupybot,
make sure your configuration directory is owned by the supybot user
and run the following command:

    docker run -d --name mysupybot \
               -v /var/lib/mysupybot \
               -d SUPYBOT_HOME /var/lib/mysupybot \
               obosob/supybot \
               supybot mysupybot.conf

or:

    docker run -d --name mysupybot \
               -v /var/lib/mysupybot:/var/supybot \
               obosob/supybot \
               supybot mysupybot.conf

The environment values are:

    SUPYBOT_CHANNELS       # Channels to join (default: empty)
    SUPYBOT_HOME           # Where to put the config files (default: /var/supybot)
    SUPYBOT_IDENT          # Identity of bot (default: supybot)
    SUPYBOT_NETWORK        # Network name (default: freenode)
    SUPYBOT_NICK           # Nick of bot (default: supybot)
    SUPYBOT_PASSWORD       # Network Password (default: empty)
    SUPYBOT_PORT           # Network Port (default: 6697)
    SUPYBOT_PREFIXES       # Single character command prefixes, can specify multiple (default: '!')
    SUPYBOT_PREFIX_STRINGS # Multi-character command prefixes, space delimited (default: empty)
    SUPYBOT_SERVER         # Network address (default: irc.freenode.net)
    SUPYBOT_USER           # Bot Username (default: supybot)
    SUPYBOT_USE_SSL        # Use SSL? (default: True)
    SUPYBOT_OWNER          # Owner identity for !identify (default: owner)
    SUPYBOT_OWNER_PASS     # Owner password for !identify (default: owner)
