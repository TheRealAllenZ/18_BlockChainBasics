# Tip to deal with Password: prompt

## First, to get past the HTTP forbidden error

In the instructions, we run the first node with this command:

`geth --datadir node1 --unlock "d84d79a0069fb5d3cf8eca3c689f231d6b603c8f" --mine --rpc`

If you get this error: ***Error: account unlock with HTTP access is forbidden***
This may need to be suffixed with the --allow-insecure-unlock parameter, like so:

`geth --datadir node1 --unlock "d84d79a0069fb5d3cf8eca3c689f231d6b603c8f" --mine --rpc --allow-insecure-unlock`

## Now, run the second node with the first node's enode address

`geth --datadir node2 --unlock "7a4f862ab163fc62dce2cfbb734ddac153c5e8cc" --mine --port 30304 --bootnodes enode://b044f481e52f03950ed88ad18f550ace268ad4e4e1647f80c5808d6ea2c4e7f550d8ed25a14608afa6e5828f1b69fdfcf5d7775394f7c38d8592f600e4a37e90@127.0.0.1:30303`

However, this will prompt for a password, and may or may not wait long enough for you to type one in.
To workaround this, create a text file in your geth folder called ***password.txt***.

Then, type the password into that file and save it.

Then, add the --password password.txt parameter to the command above.

`geth --datadir node2 --unlock "7a4f862ab163fc62dce2cfbb734ddac153c5e8cc" --mine --port 30304 --bootnodes enode://b044f481e52f03950ed88ad18f550ace268ad4e4e1647f80c5808d6ea2c4e7f550d8ed25a14608afa6e5828f1b69fdfcf5d7775394f7c38d8592f600e4a37e90@127.0.0.1:30303 --password password.txt`
