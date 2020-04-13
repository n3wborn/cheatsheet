# TMUX


### LANCEMENT

    tmux


### LEADER KEY

La *leader key* est le raccourcis clavier qui sert à *dialoguer* avec tmux.
Chaque raccourcis clavier ou *commandes* envoyé à destination de tmux doit être précédé par celle ci. Par défaut, il s'agit de **CTRL + b** .
Par exemple, pour créer une nouvelle fenêtre dans tmux, il faudra effectuer la combinaison suivante :

    ctrl + b, c



### RACCOURCIS UTILES


| COMMANDE | RACCOURCIS
| -------- | --------
| c        | Create a new window
| ?        | List all key bindings
| d        | Detach the current client
| D        | Choose a client to detach
| "        | Split the current pane into two, top and bottom.
| %        | Split the current pane into two, left and right
| n        | Change to the next window
| p        | Change to the previous window
| l        | Move to the previously selected window
| left,right,up,down    | Change to the pane left, right...
| #        | List all paste buffers
| o        | Select the next pane in the current window
| ;        | Move to the previously active pane
| '        | Prompt for a window index to select
| .        | Prompt for an index to move the current window
| 0 to 9   | Select windows 0 to 9
| $        | Rename the current session
| ,        | Rename the current window
| !        | Break the current pane out of the window
| [        | Enter copy mode to copy text or view the history
| ]        | Paste the most recently copied buffer of text
| f        | Prompt to search for text in open windows
| C-z      | Suspend the tmux client
| x        | Kill the current pane

