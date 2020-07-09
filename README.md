# Becky - The backup program

Becky makes backing up your files and databases AWS S3 easy.

## 🔗 Requirements

- [AWS account](https://aws.amazon.com/)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)

## 👨‍💻 Install

1. Install [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html).

    ```sh
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install
    rm -rf aws awscliv2.zip
    ```

    - See [AWS guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
        for uninstalling and removing.

2. Install Becky.

    ```sh
    ./configure --prefix=/usr/local
    sudo make install
    ```

## 🚀 Getting Started

1. Configure Becky by editing the config file in `/etc/becky.conf`.
    - Ensure `/etc/becky.conf` has `600` permissions since it contains sensitive information.

2. To backup your files run Becky.

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

## 👹 Caveats

- You can not backup databases that are larger than `50GB`.
- If you use `aws` CLI while Becky is running, the credentials and config
    won't work because Becky temporarily replaces `~/.aws/config` and
    `~/.aws/credentials`.

## 🔨 Development

You can create `./development.becky.conf` file and it will be read by `./becky`
so you don't have to install it.