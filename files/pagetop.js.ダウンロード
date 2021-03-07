// JavaScript Document

jQuery(window).load(function() {
	
	// ページの先頭へ
	var topBtn = jQuery('.pageTop');
	topBtn.hide();
    
	// スクロール時の動き
	jQuery(window).scroll(function () {
		if (jQuery(this).scrollTop() > 100) {
			topBtn.fadeIn();
		} else {
			topBtn.fadeOut();
		}
	});

	// クリック時の動き
	topBtn.click(function () {
		jQuery('body,html').animate({
			scrollTop: 0
		}, 500);
		return false;
	});
	
});