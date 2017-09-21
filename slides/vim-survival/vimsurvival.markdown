# vim survival guide

## Exiting vim

	<ESC> :q!

## Noob method

	i
	arrow keys
	backspace
	<ESC>
	:w
	:q

## Save our eyes (and hands?)

	:set number
	:syntax on
	:set mouse=a

## Moving around

To move the cursor, press the h,j,k,l keys as indicated.

 	      ^
 	      k		    Hint:  The h key is at the left and moves left.
	< h       l >		   The l key is at the right and moves right.
	      j			   The j key looks like a down arrow.
	      v

	w - move to next word
	b - move to previous word
	e - move to end of current word

	$ - move to end of line
	0 - move to start of line (or ^)

	CTRL+D - Page down
	CTRL+U - Page up

	CTRL+I - go forward jump
	CTRL+O - go back a jump

	G - End of file
	g - goto

## Basic editing

	i - insert mode
	v - visual mode
	d - delete
	ESC - get out (CTRL+C more ergonomic)
	c - change
	y - yank (copy)
	p - put (paste)

	u - undo
	CTRL+R - redo

	>> - indent right
	<< - indent left

## Modal

vim is modal!

	i - insert
	R - Replace
	v - visual (visible motion)

## Mental model (ha ha)

	[OPERATOR?] [COUNT/MOTION]

Using this logic, figure these out:

	5j
	53G
	2w
	cw
	dw
	d2w
	3dd

1. The quick brown
2. fox jumps over
3. the lazy dog
4. Jackdaws love my
5. big sphinx of quartz

Double operator

	yy - yank to end of line
	dd - delete to end of line
	cc - change to end of line
	gg - go to start of file

## Menu commands

	:s
	:r
	:set

Treat these as "menu" commands (eg. command palette)

## Search

Save more eyes `:set hls`

Foobar

	/foobar

foobar

	n - next
	N - previous

	/foobar/i

## Replace (substitute)

	:s/foobar/barbaz/

	/c - confirm
	/g - global
	/i - insensitive

	:s/barbaz/qixqux/igc

# Cool

## Commands

	:! - command
	:!ls

	:r - paste from file
	:r cube.txt
	:r !date

## Indent

	= - indent
	gg=G

## Split window

	:vsplit
	:hide
	CTRL+W

## Tabs

	:tab
	gt - go to previous tab
	gT - go to next tab

## Settings

	.vimrc

## Multiline cursor

	CTRL+V (visual-block)
	Select
	I<text>ESC

	abc 123
	def 234 
	ghi 456 789
	jkl 000

## File browser

	:!ls

or

	:Vexplore
	:Sex
	
	CTRL+W to tab
	:q to close

## Learn basics

	vimtutor
