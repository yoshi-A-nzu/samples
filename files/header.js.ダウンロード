// JavaScript Document

jQuery(window).on('load resize', function(){
 

	  // #headerの高さを取得
	  var getHeight = jQuery('#header').innerHeight();

	  // #main_visualの高さと縦中央
	  jQuery('#wrapper').css('padding-top', getHeight + 'px');

 
});

// JavaScript Document

jQuery(document).ready(function() {

	jQuery("#header .nav > li").on('click',function(){

		//スマホ表示時のみチェック
		var w = jQuery(window).width();
		var x = 768;
		if (w < x) {
			jQuery(this).find('.child_menu').toggleClass('menu_open');
		} 

	});

});


