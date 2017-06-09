CSS extension
Pre-processed to be understood by browser
Written in Ruby
Uses addition of variables
	$color : #somehex;
Uses nesting
	.pixgrid {
		ul {
			margin: 0;
			li {
				float: left;
				
				}
			}
		}
Features partials
	@import "variables";
Features Extend
	.btn {
		blah: blah;
	.btn-reverse {
		@extend .btn
		more blah
	}
	}
Features operators
	$thickness : 1px;
	$thicker : $thickness * 5;
Features mixins
	like macros or Ruby methods
	
