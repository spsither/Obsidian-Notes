To create a session run 
>tmux

If you want to name the session do
>tmux new -s SessionNameHere

To detach from the session do
>CTRL + b,  d
>hold ctrl, press b, let go of both of the keys, and press d

To list tmux session
>tmux ls

to attach to a session
>tmux attach

to attach to a specific session use the session name
>tmux attach-session -t sessionName

to split the pane vertically
>Ctrl + b , %

to split a pane horizontally
>Ctrl + b, "

to switch to the next pane
>Ctrl + B and type **o** Allows you to switch to the next pane

to alternate between two panes
>Ctrl + b, ;

to close a pane
>Ctrl + b, x

[tmux cheat sheet](https://tmuxcheatsheet.com/)