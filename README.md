# GitHub Email Scraper

Scrape GitHub for email addresses associated with a username. Search through public events and commits in the user's repositories.

## Requirements

-   Python 3
-   Requests (`pip3 install requests`)

## Installation

### PIP

```
pip install github-email-scraper
```

### Manual install

1. `pip install -r requirements.txt`
2. `python setup.py install` or `pip install .`

### Standalone

Just run the `github_email_scraper.py` script in the github_email_scraper directory.

## Usage

Specify a username with `-u` or a file containing usernames (one per line) with `-U`. Choose to either search commits (`--commits`), events (`--events`), or both (`--all`).

Installed

```
github-email-scraper -u USERNAME --all
```

Standalone

```
python github_email_scraper.py -u USERNAME --all
```

### Full usage

```
usage: github_email_scraper.py [-h] (-u USER | -U USER_LIST) [-c] [-e] [-a] [-o] [-n] [-r] [-l AUTH_USER] [-t TOKEN]

Scrape GitHub for email addresses associated with a username. Choose to search through public events (--events), commits in the user's repositories
(--commits), or both (--all). Specify users on the command line (-u) or load a file with one user per line (-U).

optional arguments:
  -h, --help            show this help message and exit
  -u USER, --user USER  Target GitHub username
  -U USER_LIST, --user-list USER_LIST
                        File containing list of target GitHub usernames, or - for stdin
  -c, --commits         Look through user's commits in their repos
  -e, --events          Look through user's public events
  -a, --all             Commits and events
  -o, --other-users     Include emails from commits not associated with the GitHub user. This may find other email addresses beloning to the user that they haven't manually associated with their GitHub account, but may also contain a lot of emails from other accounts if the repo is a fork or has multiple contributors.
  -n, --name            Show commit/event author name
  -r, --repo            Show repo the email was (first) found in
  -l AUTH_USER, --auth-user AUTH_USER
                        Your GitHub username to use for authentication; use with --token
  -t TOKEN, --token TOKEN
                        Your GitHub personal access token; use with --auth-user
```

## Increasing your rate limit

GitHub limits the number of unauthenticated API requests per IP address. To get around this, create a personal access token on GitHub under your user's Settings -> Developer settings -> Personal access tokens. It does not need any scopes. Then use it in this program by setting `--auth-user YOUR_GH_USERNAME --token YOUR_TOKEN`.
