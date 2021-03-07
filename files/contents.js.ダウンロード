jQuery.noConflict();
var j$ = jQuery;

j$(window).load(function() {
	
	// 画像とテキスト（スクロール付き）
	var boxheight = j$('.parts_img_type47_photo').height();
	j$('.parts_img_type47_text_scrBox').css('height', boxheight - 72);
	
	j$(window).resize(function(){
		var w = j$(window).width();
		var x = 767;
		var boxheight = j$('.parts_img_type47_photo').height();
		
		if (w <= x) {
			j$('.parts_img_type47_text_scrBox').css('height', '');
		} else {
			j$('.parts_img_type47_text_scrBox').css('height', boxheight - 72);
		}
		
	});
	
	// よくある質問（クリックで回答を表示）
	j$('.parts_text_type17 dd').css('display', 'none');
	j$('.parts_text_type17 dt').on('click', function() {
		j$(this).next().slideToggle();
	});
	
  // Indeed募集一覧
  j$(function(){
    j$('.cms_col_3').eq(0);
    j$('.cms_col_3').eq(j$('.cms_col_3').length-1);

    for(var i=0; i<j$('.cms_col_3').length; i++){
        if(i%3===0){
            j$('.cms_col_3').eq(i).addClass('rigth_ntn');
        }else if(i%3===2){
            j$('.cms_col_3').eq(i).addClass('left_ntn');
        }
    }
  });
  
});


/* ---------------------------------------------------------------------------------------- 

	2020.07 var.03

---------------------------------------------------------------------------------------- */

(function(j$) {j$(function(){
if(j$('#published').length>0){// 公開サイトのみ

// タイトルをクリックして詳細が開くパーツ
j$('.cparts-var03-type12a').each(function(){
    j$(this).nextAll().each(function(){
        if(j$(this).hasClass('cparts-var03-type12c')) return false;
        j$(this).addClass('cparts-var03-type12b');
        j$(this).hide();
    });
});
j$('.cparts-var03-type12a').next('.cparts-var03-type12b').addClass('cparts-var03-type12b-first');
j$('.cparts-var03-type12c').prev('.cparts-var03-type12b').addClass('cparts-var03-type12b-last');
j$('.cparts-var03-type12c').hide();
j$('.cparts-var03-type12a').off().on('click', function() {
    j$(this).find('.cparts-icon-block').toggleClass('cparts-icon-block-open');
    j$(this).nextAll().each(function(){
        if(j$(this).hasClass('cparts-var03-type12c')) return false;
        j$(this).slideToggle(500);
        setTimeout(function() {
        j$('.cparts-var03-type12b').css('overflow','visible');
        }, 2000);
    j$('.cparts-var03-type12a').toggleClass('cparts-var03-type12a-open');
    });
});
   

// 列1個のコンテンツパーツ
j$(window).load(function() {

var left = 0;
var maxHeight = 0;
j$('.cparts-col2-block').each(function(i, box) {
    if(i===0){
        left = j$(this).offset().left;
        start = 0;
    } else {
        if(left === j$(this).offset().left || j$('.cparts-col2-block').length == i+1) {
                if( j$('.cparts-col2-block').length == i+1 ){
                    i++;
                    if(maxHeight < j$(this).find('.col2-height').height()) maxHeight = j$(this).find('.col2-height').height();
                }
                var count = i - start;
            for(ii=(i-1);ii>=start;ii--) {
                j$('.cparts-col2-block').eq(ii).find('.col2-height').height(maxHeight);
                if (window.matchMedia( "(min-width: 992px)" ).matches) {
                    if(count === 1) j$('.cparts-col2-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col2-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
                if (window.matchMedia( "(max-width: 991px) and (min-width: 768px)" ).matches) {
                    if(count === 1) j$('.cparts-col2-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col2-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
            }
            maxHeight=0;
            start = i;
        }
    }
    if(maxHeight < j$(this).find('.col2-height').height()) maxHeight = j$(this).find('.col2-height').height();
});

var left = 0;
var maxHeight = 0;
j$('.cparts-col3-block').each(function(i, box) {
    //最初の1つ目
    if(i===0){
        left = j$(this).offset().left;
        start = 0;
    } else {
        // 1つめと同じLeftt値か最後のエレメントなら
        if(left === j$(this).offset().left || j$('.cparts-col3-block').length == i+1) {
// console.log('i:'+i);
            if (left === j$(this).offset().left && j$('.cparts-col3-block').length == i+1) j$('.cparts-col3-block').eq(i).addClass('cparts-left-ntn');
                if( j$('.cparts-col3-block').length == i+1 ){
                    if(maxHeight < j$(this).find('.cparts-col3-height').height()) maxHeight = j$(this).find('.cparts-col3-height').height();
                    i++;
               }
                var count = i - start;
// console.log('start:'+start);
// console.log('i:'+i);
// console.log('count:'+count);
            for(ii=(i-1);ii>=start;ii--) {
// console.log(count);
                j$('.cparts-col3-block').eq(ii).find('.cparts-col3-height').height(maxHeight);
                if (window.matchMedia( "(min-width: 992px)" ).matches) {
                    if(count === 1) j$('.cparts-col3-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col3-block').eq(ii).addClass('cparts-center-ntn');
                    if(count === 3) j$('.cparts-col3-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
                if (window.matchMedia( "(max-width: 991px) and (min-width: 768px)" ).matches) {
                    if(count === 1) j$('.cparts-col3-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col3-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
            }
            maxHeight=0;
            start = i;
            // count = 0;
        }
    }
    if(maxHeight < j$(this).find('.cparts-col3-height').height()) maxHeight = j$(this).find('.cparts-col3-height').height();
});


var left = 0;
var maxHeight = 0;
j$('.cparts-col4-block').each(function(i, box) {
    if(i===0){
        left = j$(this).offset().left;
        start = 0;
    } else {
        if(left === j$(this).offset().left || j$('.cparts-col4-block').length == i+1) {
                if( j$('.cparts-col4-block').length == i+1 ){
                    i++;
                    if(maxHeight < j$(this).find('.col4-height').height()) maxHeight = j$(this).find('.col4-height').height();
                }
                var count = i - start;
            for(ii=(i-1);ii>=start;ii--) {
                j$('.cparts-col4-block').eq(ii).find('.col4-height').height(maxHeight);
                if (window.matchMedia( "(min-width: 992px)" ).matches) {
                    if(count === 1) j$('.cparts-col4-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col4-block').eq(ii).addClass('cparts-l-center-ntn');
                    if(count === 3) j$('.cparts-col4-block').eq(ii).addClass('cparts-r-center-ntn');
                    if(count === 4) j$('.cparts-col4-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
                if (window.matchMedia( "(max-width: 991px) and (min-width: 768px)" ).matches) {
                    if(count === 1) j$('.cparts-col4-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col4-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
            }
            maxHeight=0;
            start = i;
        }
    }
    if(maxHeight < j$(this).find('.col4-height').height()) maxHeight = j$(this).find('.col4-height').height();
});



var left = 0;
var maxHeight = 0;
j$('.cparts-col5-block').each(function(i, box) {
    if(i===0){
        left = j$(this).offset().left;
        start = 0;
    } else {
        if(left === j$(this).offset().left || j$('.cparts-col5-block').length == i+1) {
                if( j$('.cparts-col5-block').length == i+1 ){
                    i++;
                    if(maxHeight < j$(this).find('.col5-height').height()) maxHeight = j$(this).find('.col5-height').height();
                }
                var count = i - start;
            for(ii=(i-1);ii>=start;ii--) {
                j$('.cparts-col5-block').eq(ii).find('.col5-height').height(maxHeight);
                if (window.matchMedia( "(min-width: 992px)" ).matches) {
                    if(count === 1) j$('.cparts-col5-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col5-block').eq(ii).addClass('cparts-l-center-ntn');
                    if(count === 3) j$('.cparts-col5-block').eq(ii).addClass('cparts-center-ntn');
                    if(count === 4) j$('.cparts-col5-block').eq(ii).addClass('cparts-r-center-ntn');
                    if(count === 5) j$('.cparts-col5-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
                if (window.matchMedia( "(max-width: 991px) and (min-width: 768px)" ).matches) {
                    if(count === 1) j$('.cparts-col5-block').eq(ii).addClass('cparts-left-ntn');
                    if(count === 2) j$('.cparts-col5-block').eq(ii).addClass('cparts-rigth-ntn');
                    count--;
                }
            }
            maxHeight=0;
            start = i;
        }
    }
    if(maxHeight < j$(this).find('.col5-height').height()) maxHeight = j$(this).find('.col5-height').height();
});


if (window.matchMedia( "(max-width: 991px)" ).matches) {
j$('.cparts-img-type12a').each(function(i, box) {
        var maxHeight = 0;
        j$(box).find('.cparts-txt-block').each(function() {
            if (j$(this).height() > maxHeight) maxHeight = j$(this).height();
        });
        j$(box).find('.cparts-txt-block').height(maxHeight);
});
j$('.cparts-img-type12b').each(function(i, box) {
        var maxHeight = 0;
        j$(box).find('.cparts-txt-block').each(function() {
            if (j$(this).height() > maxHeight) maxHeight = j$(this).height();
        });
        j$(box).find('.cparts-txt-block').height(maxHeight);
});
}

});


// マウスオーバーでテキスト表示
j$(window).load(function(){
j$('.cparts-var03-type19a').children('div').each(function(){
    var k = j$(this).find('.cparts-img-block').height();
j$(this).find('.cparts-body-block').css('height',k+'px');
});
j$('.cparts-var03-type19b').children('div').each(function(){
    var k = j$(this).find('.cparts-img-block').height();
j$(this).find('.cparts-body-block').css('height',k+'px');
});
});


// 公開サイトのみ
}
// メインビジュアル
	j$(".cparts-var03-type22").find(".cparts-body-block").each(function(){
			j$(this).addClass('cparts-move');
			j$(this).parents('.cparts-var03-type22').find('.cparts-img-block img').addClass('cparts-img-in');
	});
	j$(".cparts-var03-type23 .cparts-body-block").each(function(){
			j$(this).addClass('cparts-fade-in');
	});
    
j$(function() {
// テーブルブロック追加
    var tableBlock = j$('<div class="cparts-table-block"></div>');
    j$('.cparts-cell-block').not('.cparts-cell-block+.cparts-cell-block').each(function(){
      j$(this).nextUntil(':not(.cparts-cell-block)').andSelf().wrapAll(tableBlock);
    });

    // var tableInnerHTML = j$('.cparts-table-block').find('.cparts-cell-block');
    // j$(this).before(tableInnerHTML);
    // j$(this).remove();

    j$(".cparts-table-block:empty").remove();


// インライン親ブロック追加
    var colBlock = j$('<div class="cparts-col-block"></div>');
    j$('.cparts-inline-block').not('.cparts-inline-block+.cparts-inline-block').each(function(){
      j$(this).nextUntil(':not(.cparts-inline-block)').andSelf().wrapAll(colBlock);
    });

    // var colInnerHTML = j$('.cparts-col-block').find('.cparts-inline-block');
    // j$(this).before(colInnerHTML);
    // j$(this).remove();

    j$(".cparts-col-block:empty").remove();


// 流れ（ライン）ブロック追加
    var connectorBlock = j$('<div class="cparts-connector-block"></div>');
    j$('.cparts-connector--curve').not('.cparts-connector--curve+.cparts-connector--curve').each(function(){
      j$(this).nextUntil(':not(.cparts-connector--curve)').andSelf().wrapAll(connectorBlock);
    });

    // var colInnerHTML = j$('.cparts-col-block').find('.cparts-inline-block');
    // j$(this).before(colInnerHTML);
    // j$(this).remove();

    j$(".cparts-connector-block:empty").remove();
});

// 最初は全部消す
    j$('.cparts-var03-type26b').hide();
    j$('.cparts-var03-type26c').hide();
    j$('.cparts-inner').hide();
    var edit_site = j$('#cms_contents_area').length;
    if(edit_site === 0) {
        j$('.cparts-var03-type26d').hide()
        j$('.cparts-var03-type26a .cparts-notes-block').hide()
    };
    // 見出しの処理
    j$('.cparts-var03-type26a').each(function(){
        // 自身のliに対して処理を行う
        j$(this).find('ol li').each(function(i){
            // クラス名を追加する
            j$(this).addClass('cparts-select' + (i+1));
            var li = j$(this).length;
            j$(this).css('width','calc(100% / '+li+')');
            // 最初の要素にはselect-on
            if(i === 0) j$(this).addClass('cparts-select-on');
            // クリックイベントを追加
            j$(this).off().on('click', function(event) {
                // 自分のグループのselect-onを削除
                j$(this).parents('.cparts-var03-type26a').find('.cparts-select-on').removeClass('cparts-select-on');
                // 自分にselect-onを追加
                j$(this).addClass('cparts-select-on');
                var show_flag = 0; // 表示フラグ　1の間は表示する
                var show_class = j$(this).attr('class').replace(' cparts-select-on',''); // 表示するクラス名
                j$(this).parents('.cparts-var03-type26a').nextAll().each(function(index, el) {
                    if(j$(this).hasClass('cparts-var03-type26d')) return false;
                    j$(this).hide();
                });
                j$(this).parents('.cparts-var03-type26a').nextAll().each(function(index, el) {
                    if(j$(this).hasClass('cparts-var03-type26d')) return false;
                    if(j$(this).hasClass('cparts-var03-type26b') && j$(this).hasClass(show_class) && show_flag === 0) {
                        show_flag = 1;
                        if(edit_site)
                            j$(this).fadeIn(1000);
                    } else if(j$(this).hasClass('cparts-var03-type26c') && j$(this).hasClass(show_class) && show_flag === 1) {
                        show_flag = 0;
                        if(edit_site)
                            j$(this).fadeIn(1000);
                    } else if(show_flag === 1) {
                        j$(this).fadeIn(1000);
                    }
                });
                return false;
            });
        });
        var index = 1;
        j$(this).nextAll().each(function() {
            if(j$(this).hasClass('cparts-var03-type26d')) return false;
            // console.log(index);
            // j$(this).prevAll('.cparts-var03-type26a').find('li').css('width','calc(100% / '+index+')');
            if(j$(this).hasClass('cparts-var03-type26b')) {
                // j$(this).find('span').html(index);
                j$(this).addClass('cparts-select'+index);
                j$(this).attr('data','cparts-select'+index);
                if(index === 1 && edit_site) j$(this).show();
                else j$(this).hide();
            } else if(j$(this).hasClass('cparts-var03-type26c')) {
                // j$(this).find('span').html(index);
                j$(this).addClass('cparts-select'+index);
                j$(this).attr('data','cparts-select'+index);
                if(index === 1 && edit_site) j$(this).show();
                else j$(this).hide();
                index++;
            } else {
                j$(this).addClass('cparts-inner');
                if(index === 1) j$(this).show();
                else j$(this).hide();
            }
        });
    });

 j$('.cparts-var03-type26a .cparts-notes-block p').off().on('click', function() {
    if(j$(this).hasClass('cparts-all-open')){
        j$(this).html('タブ内容を展開する（公開サイトには表示されません）');
        j$(this).removeClass('cparts-all-open');
        j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26b').hide();
        j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26c').hide();
        j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-inner').hide();
        j$(this).parents('.cparts-var03-type26a').next('.cparts-var03-type26b.cparts-select1').nextAll().each(function() {
            if(j$(this).hasClass('cparts-var03-type26c')) return false;
            j$(this).show();
        });
        j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26b.cparts-select1').show();
        j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26c.cparts-select1').show();
        j$('.cparts-var03-type26a ol li').removeClass('cparts-select-on');
        j$('.cparts-select1').addClass('cparts-select-on');
    }else{
    j$(this).html('プレビューを表示（公開サイトには表示されません）');
    j$(this).addClass('cparts-all-open');
    j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26b').show();
    j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-var03-type26c').show();
    j$(this).parents('.cparts-var03-type26a').nextAll('.cparts-inner').show();
    }
});

//目次パーツ　高さ合わせる
j$(window).load(function() {
    j$('.cparts-var03-type18').each(function() {
        var maxHeight = 0;
        j$(this).find('.cparts-body-block').each(function() {
            if (j$(this).height() > maxHeight) maxHeight = j$(this).height();
        });
        j$(this).find('.cparts-body-block').height(maxHeight);
    });
});

});
})(jQuery);


/* ---------------------------------------------------------------------------------------- 

	2021.01 var.04

---------------------------------------------------------------------------------------- */
(function($) {$(function(){

  // 画像／見出し・背景付テキスト_ver.2・見出し・背景付テキスト／画像_ver.2：上余白調整
  if (window.matchMedia( "(min-width: 768px)" ).matches) {
$(window).load(function() {
  $('.parts_img_type37').each(function() {
  var himg = $(this).find('img').height();
  var h = $(this).find('.parts_img_type37_text').height();
  var m = h - himg +24;
console.log(m);
console.log(himg);
  if (himg < h) {
    $(this).find('img').css('margin-top', m+'px');
  }
  });

  $('.parts_img_type36').each(function() {
  var himgb = $(this).find('img').height();
  var hb = $(this).find('.parts_img_type36_text').height();
  var mb = hb - himgb +24;
  if (himgb < hb) {
    $(this).find('img').css('margin-top', mb+'px');
  }
  });
});
  }
  
});})(jQuery);