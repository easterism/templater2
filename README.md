templater2
==========

Pure PHP Templater

test.tpl

	Title
	<ul>
	<!--BEGIN li-->
	<li>
		WWW
		<!--BEGIN div-->
		<div>[key]
			<!--BEGIN deep-->
			<span>@</span>
			<!--END deep-->
		</div>
		<!--END div-->
	</li>
	<!--END li-->
	</ul>

Usage:

	$tpl = new Templater2();
	$tpl->loadTemplate('test.tpl');
	$tpl->li->assign('WWW', 'value1'); //replace the 'WWW' by the 'value1' string inside the 'li' block
	$tpl->li->reassign(); //initial loop for 'li'
	$tpl->li->assign('WWW', 'another li');
	$tpl->li->div->assign('[key]', 'content');
	$tpl->li->div->reassign(); //initial loop for 'div' inside 'li'
	$tpl->li->div->assign('[key]', 'content');
	$tpl->reassign(); //initial loop for whole template
	$tpl->assign('Title', 'Another UL'); //
	$tpl->li->assign('WWW', '');
	$tpl->li->div->assign('[key]', '');
	$tpl->li->div->deep->assign('@', 'I\'m a deepest span');

	echo $tpl->parse();
	
