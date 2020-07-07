# Becky - The backup program

Becky makes backing up your files and databases AWS S3 easy.

## 💎 Requirements

- [s3cmd](https://github.com/s3tools/s3cmd)
- [AWS account](https://aws.amazon.com/)

## 👨‍💻 Install

1. Install [s3cmd](https://github.com/s3tools/s3cmd).

    ```sh
    sudo pip3 install s3cmd
    ```

2. Install Becky.

    ```sh
    configure --prefix=/usr/local
    sudo make install
    ```

## 🚀 Getting Started

1. Configure `s3cmd` with either the interactive tool `s3cmd --configure` or copy
the config file to `~/.s3cfg`.
    
    - Ensure `~/.s3cfg` has `600` permissions since it contains sensitive information.
    - See [s3tools.org](https://s3tools.org) for [example configuration file](https://s3tools.org/kb/item14.htm).

2. Configure Becky by editing the config file in `/etc/becky.conf`.
    - Ensure `/etc/becky.conf` has `600` permissions since it contains sensitive information.

3. To backup your files run Becky.

    ```sh
    becky
    ```

## ⏰ Backing up periodically

You can use [cron](https://en.wikipedia.org/wiki/Cron) to schedule Becky to run at certain time.

If you need help with the crontab syntax, you can use [crontab.guru](https://crontab.guru).

To add a new job run this command:

```
sudo crontab -e
```

Then you can e.g. add the following line to run Becky every Monday at 02:00 (2am).

```
0 02 * * 1 /usr/local/bin/becky
```