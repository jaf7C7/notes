# How To Configure A Great Minimal Vim

```
" ~/.vimrc

" Act like `vi(1)`.
set compatible

" Make `shiftwidth` follow `tabstop`.
set shiftwidth=0

" Automatically indent new lines.
set autoindent

" Don't complain about unsaved changes when switching buffers.
set hidden

" Automatically re-read current file on events like `^Z`, `fg` etc. This
" is great if you have an external file-watcher formatting files.
" Some autocommands to try if you want the buffer to update without leaving vim:
" - Re-read current file after cursor is inactive for 'updatetime':
" 	au CursorHold,CursorHoldI * checktime
" - Re-read the current file when cursor is moved in any mode:
" 	au CursorMoved,CursorMovedC,CursorMovedI * checktime
set autoread

" Autocomplete in command-mode with `Tab`.
set wildchar=<Tab>

" Save 100 previous commands.
set history=100

" Reformat comments with `gq<motion>` and comment leader `# `.
set formatprg=fmt\ -p\\\\#\\\

" Allow `more` prompt for scrolling info screens (e.g. `:highlight`).
set more

" Set nicer characters for whitespace display.
set listchars=tab:»\ ,space:·

" Just use terminal colors 0-7.
set t_Co=8

" Tell vim the terminal background is dark to change the colours it uses.
set background=dark

" Change a few ui colours (see :help 'highlight').
set highlight=vr,+ri,=rb,x-,Xr'

" Turn off distracting syntax highlighting.
if has('syntax')
    syntax off
endif
```


