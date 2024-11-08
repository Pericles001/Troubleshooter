### Steps to Run a Script in `tmux` and Keep It Running

1.  **Start a `tmux` session**:

    bash

    Copy code

    `tmux new -s my_session_name`

    This command creates a new `tmux` session named `my_session_name` (you can choose any name you like).

2.  **Run your Python script**:

    bash

    Copy code

    `python scripts/automate_train.py`

    Start your training script as usual. Since you're inside a `tmux` session, the process will continue even if you disconnect from the server.

3.  **Detach from the `tmux` session**:

    -   Press `Ctrl + B`, then release and press `D`.
    -   This detaches you from the `tmux` session but keeps it running in the background.
4.  **Log out or disconnect from the server**: You can safely disconnect now. The `tmux` session with your running script will continue independently.

5.  **Reattach to the `tmux` session later**:

    -   When you reconnect to the server, you can reattach to your `tmux` session to check on your script's progress.

    bash

    Copy code

    `tmux attach -t my_session_name`

6.  **Optional: List all `tmux` sessions** (if you forget the name or have multiple sessions):

    bash

    Copy code

    `tmux ls`


To see a list of all active `tmux` sessions, use the following command:

bash

Copy code

`tmux list-sessions`

or the shorter version:

bash

Copy code

`tmux ls`



### Example Output

plaintext

Copy code

`0: 1 windows (created Thu Nov  8 12:00:00 2023) [80x24]
1: 2 windows (created Thu Nov  8 12:15:00 2023) [80x24]`

Here, the first number (`0`, `1`, etc.) is the session ID. You can use this ID to attach to a specific session, like so:

bash

Copy code

`tmux attach-session -t 0`

Or if you named the session, you can attach by name:

bash

Copy code

`tmux attach-session -t my_session_name`