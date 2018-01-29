## Remember the MANTRA: act, repeat, reverse

### Moved to tip 8. 
Chapter 7 explained the Normal mode. Nothing special, but a good analogy with the painter.

### Tip 8 talked about chunking the 'undo's. 
The good advice is "If you paused for long enough to ask if you should leave the Insert mode, then do it"
Each insert creates the undo chunk. However arrow keys in Insert mode will also create an undo chunk

### Tip 9 talked about composing repeatable changes. 
For example to pick the "winner" command between the several commands wich acoomplish the same result you need to look into how easy will it be to repeat the edit. 'dbx' vs 'bdw' vs 'daw'
 
### Moved to tip 10
That's a test from tip 10. The number 5. Apparently you can add (`<C-a>`) or substract (`<C-x>`) from number on a line. 
Vim will jump to the first number it finds on the line
 
### Tip 12 Case/Indent
Skipping the tip 11 as it talked about common sense in using count vs repeat commands  
**Operator + Motion = Action**  
Vim grammar rule: when an operator command is invoked in duplicate, it acts upon the current line.  
Upper/Lower/Switch case = gU/gu/g~  
Shift right/left/autoindent = \>/\</=  

### Tip 13 Another Backspace
Nice new command, which equals to Backspace - `<C-h>`. It also works in bash

### Tip 14 'zz'
Vim also has 'Insert Normal Mode'. This mode allows to exec one command and immediately switch back to Insert mode. To swich to this mode from Insert mode press `<C-o>`
Other interesting command is 'zz'. It will redraw the screen with current line in the middle of the window.

### Tip 15 Navigate line (f/t)
Reminding about motion command 't'. It's the same as f, but doesn't include the character to jump to. [yt,] can be read as yank to/till ',' character, not including it. 
The other useful shortcut is `<C-r>`{register} will paste from the register {register}. For yank register use 0.

### Tip 16 Expression Register
This one talks about expression register, which can evaluate vim script expression. Can be invoked from Insert mode by `<C-r>=`. For example `<C-r>=6\*35<CR>` will paste 210 as the result of expression

### Tip 17 & 18 Character Codes
`<C-v>{code}` will insert the 3-digit character code. You can specify the character in hex code - `<C-v>`u{1234}. For example `<C-v>u0041` to insert 'A' character. To print the numeric code of the character use command 'ga'.
We can also paste unusual characters by Digraph. To paste it use `<C-k>{char1}{char2}`. Try 12, 14 or 34

### Tip 19 Replace Mode
Replacing text. To replace the character use 'r' command to replace character under cursor. If you press 'R' it will invoke Replace mode, which is equal to pressing 'Insert' keyboard button. The 'Insert' keyboard button will toggle replace/insert mode

Chapter 4. Visual Mode
### Tip 20 - Grok the Visual Mode :)

### Tip 21
Apparently there are several Visual modes in VIM: regular select (v), line select (V), block select (C-v). Pressing 'o' will switch the end of the visual selection (toggle free end of selection)

### Tip 27 Vim Ex Mode
It can be accessed via ':'.

The common commands:

    :[range]delete [x]      - delete specified lines [into register x]
    :[range]yank [x]        - yank specified lines [into register x]
    :[line]put [x]          - put the text from register x after specified line
    :[range]copy {address}  - copy the specified lines to below the line specified by {address}
    :[range]move {address}  - move the specified lines to below the line specified by {address}
    :[range]join            - join the specified lines
    :[range]normal {cmds}   - exec Normal mode commands on each line

    :[range]substitute/{pattern}/{string}/[flags]   - Replace occurrences of {pattern} with {string} on each specified line
    :[range]global/{pattern}/[cmd]                  - Execute the Ex command [cmd] on all specified lines where teh {pattern} matches

### Tip 28 Execute commands on one or more consecutive lines
Specify the number before command (:2p) and vim will first jump to that line. 'p' can be replaced with any other command. 
    - '$' denotes the last line in the buffer.
    - The line number can be replaced with a range (:1,4p) inclusive. We can mix and match line numbers, marks and patterns while defiing the ranges. The range is alvays a contiguous lines.
    - '%' denotes the whole buffer range.
    - '.' means current line; '0' - virtual line above first line of the file
    - If you select a range with visual selection and press ':' after that, the ex command will automatically include :'<,'> which denotes the visual selection.
    - Vim also accepts a pattern as the address: :/patter-start/,/pattern-end/
    - We can modify the address using an offset of the form: {address}+n. If n is omitted, it default to 1

### Tip 29 Duplicate/Move with ':t' and ':m' commands

### Tip 30 **Missing** for now - it talks about running Normal mode commands

### Tip 31 Repeat the last Ex Command
@: will repeat the last ex command. After running it the first time it can be repeated with the @@

### Tip 32 Tab-Complete the Ex Commands
Vim supports tab completion. Scroll backward via `<S-Tab>`
_<C-d>_ asks Vim to reveal a list of possible completions (it will display either command or options)

### Tip 33 Insert the Current Word in command prompt with `<C-r><C-w>`; `<C-a>` insert WORD

### Tip 34 Recall Commands from History
Switch to command-line mode with ':'. Pressing \<Up\> or \<Down\> will scroll over the command history. Typing start symbols and then pressing \<Up\>/\<Down\> will search by the starting symbols only (for example [h] will show all commands starting withe 'h'). The same works for search history (instead of : use /).

_The command-line window_ is invoked with 'q:' or 'q/' for command-line or search history respectively. The contects of the history can be modified in that window. Pressing \<CR\> will invoke the command on current line in that window. The window is modal. Can close window with :q or <CR>. Pressing <C-f> while in command-line mode will open the command-line window with the entered command.

### _Intermediate tips are pending :)_

### Tip 54 Vim Marks
Vim's marks allow to jump to the locations of interest. You can set the mart with `m{a-zA-Z}`.  
The `` ` `` vs ` ' ` => [move to row and column] vs [move to row only]  **That's why in Ex mode `'<,'>` selects the previous visual selection**  
Lowercase -> local to current buffer; Uppercase -> accessible globally  
Jump to the mark - `` `{mark} ``; nice to remember `mm` and `` `m `` command pair (set mark `m` and jump to this mark)

Automatic marks: 
- ``` `` ``` (position before last jump in current file)
- `` `. `` (location of last change)
- `` `^ `` (location of last insert)
- `` `< `` and `` `> `` (start and end of visual selection)

### Tip 55 Matching Parentheses with %
