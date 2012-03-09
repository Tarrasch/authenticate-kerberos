## Kerberos authentication in haskell

Authentication through the kerberos service. This repo is meant to be
used if the actual authentication service is set up by somebody else
and you just want to authenticate against it. This is just a wrapper
around the `kinit` command.

### Preconfiguration

Please first make certain that you have setup your `/etc/krb5.conf`
file. My univeristy provide this [guide] for example.

### Usage (ghci session)

    Prelude> import Web.Authenticate.Kerberos
    Prelude Web.Authenticate.Kerberos> import Data.Text
    Prelude Web.Authenticate.Kerberos Data.Text> loginKerberos (pack "username") (pack "password")
    Login sucessful
    Prelude Web.Authenticate.Kerberos Data.Text> loginKerberos (pack "wrongun") (pack "password")
    Wrong username
    Prelude Web.Authenticate.Kerberos Data.Text> loginKerberos (pack "username") (pack "wrongpw")
    Wrong password

### Usage with yesod

See the kerberos specific [yesod-auth repo].

[yesod-auth repo]: https://github.com/Tarrasch/yesod-auth-kerberos
[guide]: https://www.chalmers.se/insidan/SV/arbetsredskap/it/bastjanster/pdb-cdks/installning-av

