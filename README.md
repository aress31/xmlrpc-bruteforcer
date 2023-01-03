# xmlrpc-bruteforcer

<a href="https://www.python.org"><img alt="lang" src="https://img.shields.io/badge/Lang-Python-blue.svg"></a>
<a href="https://opensource.org/licenses/Apache-2.0"><img alt="license" src="https://img.shields.io/badge/License-Apache%202.0-red.svg"></a>

## Bruteforcing `CMS` users' passwords via the `XMLRPC` interface.

This script is a `PoC` for the _Brute Force Amplification Attack_ exploit against `XMLRPC` interfaces enabling the `_system.multicall()_` method (enabled by default).

The `_system.multicall()_` method allows multiple calls to be sent within a single `HTTP` request. Using this "wrapper", malicious attackers can carry out a large number of login attempts (bruteforce) with a minimal network impact, consequently making them stealthier and more efficient.

At the moment, the maximum number of calls which can be encapsulated within the `_system.multicall()_` method without triggering a networking error is `1999` calls meaning that for each `HTTP` request sent `1999` different login attempts are performed.

More information about the bruteforce amplification attack can be found at:

- https://blog.cloudflare.com/a-look-at-the-new-wordpress-brute-force-amplification-attack/

> [!IMPORTANT]
> This script has been sucessfully tested against WordPress versions **< 4.4**.

## Installation

1. Download this repository:

   ```bash
   git clone https://github.com/AresS31/xmlrpc-bruteforcer
   cd .\xmlrpc-bruteforcer
   ```

2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

## Running on Docker

```bash
cd .\xmlrpc-bruteforcer
docker build -t xmlrpc-bruteforcer .
docker run --rm -v $(pwd):/wordlists xmlrpc-bruteforcer -u admin -w /wordlists/wordlist.txt -t 3 -x https://wordpress.local/xmlrpc.php
```

## Usage

```bash
python3 xmlrpc-bruteforcer.py -u [username] -w [wordlist] -x [xmlrpc_intf] -t [threads_number] -c [chunks_size] -v [verbose] -h [help]
[-u]: username of the targeted user, required
[-w]: wordlist containing the passwords to try, required
[-x]: xmlrpc interface to attack, required
[-t]: number of threads to run, optional, default value: 5
[-c]: number of calls to encapsulate within a system.mullticall() call, optional, default value: 1999
[-v]: print debugging information, optional, default value: False
[-h]: print help
```

## Roadmap

- [ ] Improve the quality of the source code.

## Sponsor 💖

If you want to support this project and appreciate the time invested in developping, maintening and extending it; consider donating toward my next cup of coffee. ☕

It is easy, all you got to do is press the `Sponsor` button at the top of this page or alternatively [click this link](https://github.com/sponsors/aress31). 💸

## Reporting Issues

Found a bug? I would love to squash it! 🐛

Please report all issues on the GitHub [issues tracker](https://github.com/aress31/xmlrpc-bruteforcer/issues).

## Contributing

You would like to contribute to better this project? 🤩

Please submit all `PRs` on the GitHub [pull requests tracker](https://github.com/aress31/xmlrpc-bruteforcer/pulls).

## License

See [LICENSE](LICENSE).
