var domain_name = 'www\x2eakatake\x2eco\x2ejp';

var http_url = 'https://www.akatake.co.jp';
var https_url = 'https://www.akatake.co.jp';
var php_path = '/_administrator/connector.php';
var connector = '/_administrator/connector.php';
var base_url = '';
var site_path = '';
var cookie_first_url = 'cms_first_url';
window.addEventListener('load', function(event) {
	if($('selecter') instanceof jQuery) {
		jQuery.noConflict();
	}
});

// Smart Phone用モバイルサイトへのリンク
var strUA = navigator.userAgent.toLowerCase();
Event.observe(window,'load',function(){
if( !!document.getElementById('published') )
{
if( strUA.match(/iphone/) || strUA.match(/ipod/) || strUA.match(/android/) )
{
	var div = document.createElement('div');
	div.id = 'cmsMobileButton';
	div.style.textAlign = 'center';
	div.style.height = '50px';
	var a = document.createElement('a');
	a.href = 'https://www.akatake.co.jp/index.php?a=free_page/goto_mobile&referer='+encodeURI(location.href);
	a.innerHTML = '表示：モバイル';
	div.appendChild(a);
	document.body.appendChild(div);
	a.style.margin = '30px auto';
	a.style.padding = '5px 10px';
	a.style.border = '1px solid #233656';
	a.style.width = 'auto';
	a.style.color = '#ffffff';
	a.style.backgroundColor = '#394d68';
	a.style.backgroundImage = '-webkit-gradient(linear, left top, left bottom, from(#5e789f), to(#42566f))';
	a.style.fontSize = '12px';
	a.style.borderRadius = '4px';
	a.style.WebkitBorderRadius = '4px';
	a.style.textShadow = '#000000 0 -1px 1px';
	a.style.textDecoration = 'none';

}
}
});
var mobile = false;
if( strUA.match(/iphone/) || strUA.match(/ipod/)  || strUA.match(/ipad/) || strUA.match(/android/) )
{
	mobile = true;
function pointerX(event) {
    var docElement = document.documentElement;
     body = document.documentElement || document.body || { scrollLeft: 0 };

    if (event.changedTouches) return (event.changedTouches[0].clientX +
      (docElement.scrollLeft || body.scrollLeft) -
      (docElement.clientLeft || 0));

    return event.pageX || (event.clientX +
      (docElement.scrollLeft || body.scrollLeft) -
      (docElement.clientLeft || 0));
  }

  function pointerY(event) {
    var docElement = document.documentElement;
     body = document.documentElement || document.body || { scrollTop: 0 };

    if (event.changedTouches) return (event.changedTouches[0].clientY +
      (docElement.scrollLeft || body.scrollLeft) -
      (docElement.clientLeft || 0));

    return  event.pageY || (event.clientY +
       (docElement.scrollTop || body.scrollTop) -
       (docElement.clientTop || 0));
  }
}
// do_action
function do_action (act,title) {
	self.location.href='?q='+act;
	if(title != undefined ){
		var win = parent.Windows.getFocusedWindow();
		win.setTitle(title);
	}
}

/*
 * Ajax Request ( Return Scripts )
 *
 *--------------------------------------------------------- */

/**
 * ajax_eval ajaxでconnectorと通信し、レスポンスをeval実行する。
 *
 * ajax_eval( string data, boolean async )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param boolean 非同期フラグ true: 非同期通信 false: 同期通信
 *
 * @return void
 */
function ajax_eval( data, async )
{
	if( async == null ) async = true;
	if( !data.match(/&q=/) ) data = '&q='+data;
	new Ajax.Request(connector, {
		method: 'post',
		postBody : data,
		asynchronous  : async,
		onSuccess : function(obj){
			if(obj.responseText){
				eval(obj.responseText);
			}
		}
	});
}
function ajax_eval_debug( data, async )
{
alert(connector);
alert(data);
	if( async == null ) async = true;
	if( !data.match(/&q=/) ) data = '&q='+data;
	new Ajax.Request(connector, {
		method: 'post',
		postBody : data,
		asynchronous  : async,
		onSuccess : function(obj){
alert(obj.responseText);
			if(obj.responseText){
alert(obj.responseText);
			eval(obj.responseText);
			}
		}
	});
}
/**
 * ajax_json_eval ajaxでconnectorと通信し、レスポンスをJSON形式で取得しeval実行する。
 *
 * ajax_json_eval( string data )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 *
 * @return void
 */
function ajax_json_eval( data ) {
	if( !data.match(/&q=/) ) data = '&q='+data;
	new Ajax.Request(connector, {
		method: 'post',
		postBody : data,
		onSuccess : function(obj){
			if(obj.responseText){
				eval('ret='+obj.responseText);
				if( ret.type == 'script' ) {
					eval(ret.data);
				} else {
//					alert(obj.responseText);
				}
			}
		}
	});
}

/**
 * ajax_callback ajaxでサーバーと通信し、レスポンスをコールバック関数に引渡しする。
 *
 * ajax_callback( string data, string func, boolean async )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param string 関数名
 * @param boolean 非同期フラグ true: 非同期通信 false: 同期通信
 *
 * @return void
 */
function ajax_callback( data, func, async ) {
	if( async == null ) async = true;
	if( !data.match(/&q=/) ) data = '&q='+data;
	new Ajax.Request(connector, {
		method: 'post',
		postBody : data,
		asynchronous  : async,
		onSuccess : eval(func)
	});
}

/**
 * ajax_update ajaxでサーバーと通信し、レスポンスを指定したDOMエレメントに挿入する。
 *
 * ajax_update( string data, string elm )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param object innerHTMLを置換するエレメントのID属性値
 *
 * @return void
 */
function ajax_update( data, elm ){
	if( !data.match(/&q=/) ) data = '&q='+data;
	new Ajax.Updater(
		{success:elm},
		connector, {
			method: "post",
			postBody : data,
			evalScripts: true,
			onFailure:function(httpObj){
				$(elm).innerHTML = "Error!!";
			}
		}
	);
}

/**
 * ajax_eval ajaxでconnectorと通信し、レスポンスをeval実行する。公開サイト用。。。
 *
 * ajax_eval( string data, boolean async )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param boolean 非同期フラグ true: 非同期通信 false: 同期通信
 *
 * @return void
 */
function ajax_eval_p( data, async )
{
	if( async == null ) async = true;
	if( !data.match(/&a=/) ) { data = '&a='+data; }
	new Ajax.Request('/index.php',
	{
		method: 'get',
		 parameters : data,
		 asynchronous  : async,
		 onSuccess: function(obj) {
			if(obj.responseText){
//			alert(obj.responseText);
			eval(obj.responseText);
			}
		}
	});
}
/**
 * ajax_update_p ajaxでサーバーと通信し、レスポンスを指定したDOMエレメントに挿入する。公開サイト用。。。
 *
 * ajax_update_p( string data, string elm )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param object innerHTMLを置換するエレメントのID属性値
 *
 * @return void
 */
function ajax_update_p( data, elm )
{
	if( !data.match(/&q=/) ) data = '&a='+data;
	new Ajax.Updater(
		{success:elm},
		'/index.php', {
			method: "get",
			parameters : data,
			evalScripts: true,
			onFailure:function(httpObj){
				$(elm).innerHTML = "Error!!";
			}
		}
	);
}

function ajax_submit_p(form_obj){
    post_data = Form.serialize(form_obj);
	new Ajax.Request('/index.php', {
		method: 'post',
		postBody : post_data,
		onSuccess : function(obj){
			if(obj.responseText){
				eval(obj.responseText);
			}
		}
	});
}



/**
 * ajax_dialog dataで指定したパラメータのレスポンスをダイアログで開く
 *
 * ajax_dialog( string data, integer x, integer y )
 *
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param integer 開くダイアログの幅(px)　デフォルト480px
 * @param integer 開くダイアログの高さ(px)　デフォルト320px
 *
 * @return void
 */
var mydialog;
function ajax_dialog(data,x,y)
{
	if( !data.match(/&q=/) ) data = '&q='+data;
	if( !x ) x = 480;
	if( !y ) y = 320;
	Dialog.info(
		{
			url: connector,
			options: {
				method: 'post',
				postBody : data,
				asynchronous : false,
				evalScripts: true,
				buttonClass: 'cms-btn'
			}
		},
		{
			className:"alert",
			width:x,
			height:y,
			zIndex:10000
		}
	);
}

/**
 * ajax_submit FormをajaxでPOSTし、結果をeval実行する
 *
 * ajax_submit( obj form )
 *
 * @param obj フォームオブジェクト
 *            ※フォーム内に<input type="hidden" name="do" value="クラス名/メソッド名" />の記述があること
 *
 * @return void
 */
function ajax_submit(form_obj){
    post_data = Form.serialize(form_obj);
	new Ajax.Request(connector, {
		method: 'post',
		postBody : post_data,
		onSuccess : function(obj){
			if(obj.responseText){
				eval(obj.responseText);
			}
		}
	});
}

/**
 * ajax_submit FormをajaxでPOSTし、レスポンスを指定したDOMエレメントに挿入する。
 *
 * ajax_submit( string data, obj form, string elment)
 *
 * @param obj フォームオブジェクト
 *            ※フォーム内に<input type="hidden" name="do" value="クラス名/メソッド名" />の記述があること
 *
 * @return void
 */
function ajax_submit_update( data, formelm, elm ) {
	if( !!$('easy_html') && !!oEditor ) {
		$('easy_html').value = oEditor.GetXHTML();
		oEditor=null;
	} else if ( !!$('cmp_html') && !!oEditor ) {
		$('cmp_html').value = oEditor.GetXHTML();
		oEditor=null;
	}
	if( !data.match(/&q=/) ) data = '&q='+data+'&'+Form.serialize(formelm);
	new Ajax.Updater(
		{success:elm},
		connector, {
			method: "post",
			postBody : data,
			evalScripts: true,
			onFailure:function(httpObj){
				$(elm).innerHTML = "Error!!";
			}
		}
	);
	return false;
}

/**
 * alert_dialog アラートダイアログを表示する
 *
 * alert_dialog( string message[, integer height[, string function]] )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 * @param integer ダイアログの高さ（省略時100px)
 * @param string OKボタン押下時に実行する関数名もしくは匿名関数(function(){...})
 *
 * @return void
 */
function alert_dialog(msg, h, func) {
	if( !h ) h = 150;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.alert(msg, {
	windowParameters: {width:480, height:h, zIndex:1000000},
	className:"alert",
	id:"alert",
	okLabel: "OK",
	ok: func,
	buttonClass: 'cms-btn'
	});
}
/**
 * alert_dialog_reload アラートダイアログを表示し、OKボタン押下で画面をリロードする
 *
 * alert_dialog_reload( string message[, integer height] )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 * @param integer ダイアログの高さ（省略時100px)
 *
 * @return void
 */
function alert_dialog_reload(msg, h) {
	if( !h ) h = 150;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.alert(msg, {
	windowParameters: {width:480, height:h, zIndex:1000000},
	className:"alert",
	id:"alert",
	okLabel: "OK",
	buttonClass: 'cms-btn',
	ok: function(){ location.reload(); }
	});
}
/**
 * confirm_dialog 確認ダイアログを表示する
 *
 * confirm_dialog( string message[, integer height[, string function]] )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 * @param integer ダイアログの高さ（省略時100px)
 * @param string OKボタン押下時に実行する関数名もしくは匿名関数(function(){...})
 *
 * @return void
 */
function confirm_dialog(msg, func, h) {
	if( !h ) h = 150;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.confirm(msg, {
	windowParameters: {width:480, height:h, zIndex:1000000, duration:0.1},
	className:"alert",
	id:"alert",
	okLabel: "OK",
	ok:func,
	cancelLabel: "キャンセル",
	buttonClass: "cms-btn",
	cancel:function(){Dialog.closeInfo();}
	});
}
/**
 * confirm_dialog_update 確認ダイアログを表示し、OKボタン押下でサーバーとajax通信しレスポンスを指定したDOMエレメントに挿入する。
 *
 * confirm_dialog_update( string message, string data, string element[, integer height] )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 * @param string アクション/メソッドのパラメータ（ex. site_manager/add_site )
 * @param object innerHTMLを置換するエレメントのID属性値
 * @param integer ダイアログの高さ（省略時100px)
 *
 * @return void
 */
function confirm_dialog_update(msg, data, elm, h) {
	if( !h ) h = 150;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.confirm(msg, {
	windowParameters: {width:320, height:h, zIndex:1000000},
	className:"alert",
	id:"alert",
	okLabel: "OK",
	cancelLabel: "キャンセル",
	buttonClass: "cms-btn",
	ok:function(){ajax_update(data,elm);Dialog.closeInfo();},
	cancel:function(){Dialog.closeInfo();}
	});

}
/**
 * info_dialog 情報ダイアログを表示する
 *
 * info_dialog( string message[, integer width][, integer height][, boolean progress] )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 * @param integer ダイアログの幅（省略時320px)
 * @param integer ダイアログの高さ（省略時100px)
 * @param boolean ダイアログ内にプログレスアイコンを表示するか否か
 *
 * @return void
 */
function info_dialog(msg, w, h, progress) {
	if( !w ) w = 320;
	if( !h ) w = 150;
	if( progress !== false ) progress = true;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.info(msg, {
	className:"alert",
	id:"alert",
	buttonClass: 'cms-btn',
	windowParameters: {width:w, height:h, zIndex:1000000},
	showProgress:progress
	});
}
function sub_dialog(msg,x,y) {
	if( !x ) x = 320;
	if( !y ) y = 100;
	if(jQuery('#alert').length > 0) jQuery('#alert').attr('id','alert-bf');
	Dialog.info(msg, {
	className:"alert",
	id:"alert",
	buttonClass: 'cms-btn',
	windowParameters: {width:x, height:y, zIndex:1000000},
	showProgress:false
	});
}
/**
 * close_dialog 情報ダイアログのメッセージを変更して1.5秒後に閉じる
 *
 * close_dialog( string message )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 *
 * @return void
 */
function close_dialog(msg) {
	if(jQuery('#modal_dialog_message').length > 0){
		Dialog.setInfoMessage(msg);
	} else {
		jQuery('.alert_message').html(msg);
		jQuery('.alert_buttons').html('');
	}
	setTimeout("Dialog.closeInfo()", 1500);
}
/**
 * set_message 情報ダイアログのメッセージを変更する
 *
 * set_message( string message )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 *
 * @return void
 */
function set_message(msg,loading){
	if(jQuery('#modal_dialog_message').length > 0){
		Dialog.setInfoMessage(msg);
	} else {
		jQuery('.alert_message').html(msg);
		jQuery('.alert_buttons').html('');
		if(loading){
			jQuery('.alert_buttons').html("<div id='modal_dialog_progress' class='alert_progress'>  </div>");
		}
	}
}
/**
 * result_message 開いているダイアログにメッセージと閉じるボタンをセットする
 *
 * result_message( string message )
 *
 * @param string ダイアログ内に表示するメッセージ（HTML可）
 *
 * @return void
 */
function result_message(msg,okscript){
	if(okscript.length==0) okscript = 'Dialog.closeInfo()';
	var content = "<div class='alert_message'>" + msg  + "</div>"
				+ "<div class='alert_buttons'>"
				+ "<input type='button' value='OK' onclick='" + okscript + "' class='cms-btn'/>"
				+ "</div>";
	if(jQuery('#modal_dialog_message').length > 0){
		Dialog.setInfoMessage(content);
	} else {
		jQuery('#alert_content').html(content);
	}
}
/**
 * set_size_dialog ダイアログのサイズを変更する
 *
 * set_size_dialog( string element_id )
 *
 * @param string エレメントID、もしくはオブジェクト
 *
 * @return void
 */
function set_size_dialog(w,h)
{
	var winobj = self.Windows.getFocusedWindow();
	if( winobj === null ) return;
	winobj.setSize(w,h);
	winobj.showCenter();
}
/**
 * toggle エレメントの表示/非表示を切り替える
 *
 * toggle( string element_id )
 *
 * @param string エレメントID、もしくはオブジェクト
 *
 * @return void
 */
function toggle(elm)
{
	if( Element.visible(elm) )
	{
		$(elm).hide();
	}
	else
	{
		$(elm).show();
	}
}



function set_cookie(keyname, data, expire_flag)
{
	theDay   = 1;
	setDay = new Date();
	setDay.setTime(setDay.getTime()+(theDay*1000*60*60*24));
	expDay = setDay.toGMTString();
	val = get_cookie(keyname);
	if( val !== '' ) {
		var re = new RegExp(keyname + "="+escape(val)+";");
		document.cookie.replace(re,'');
	}
	if( !!expire_flag) {
		document.cookie = keyname + "="+escape(data)+";expires=" + expDay + "; path=/";
	} else {
		document.cookie = keyname + "="+escape(data)+ "; path=/";
	}
}
function get_cookie(keyname)
{
	theData   = "";
	theName   = keyname+"=";
	theCookie = document.cookie+";";
	start = theCookie.indexOf(theName);
	if (start != -1)
	{
		end = theCookie.indexOf(";",start);
		theData = unescape(theCookie.substring(start+theName.length,end));
	}
	return theData;
}


function open_dialog(url, x, y, title, status, modal, dialog_name, reload )
{
	if( typeof context_menu == 'object' ) context_menu.oncontextmenu_hide(); 
	if( !url ) return false;
	if( !x ) x = '1000';
	if( !y ) y = '640';
	var scr = screenInfomation();
	y = scr.nowHeight - 30;
	if( x.toString().match(/([0-9]+)%/) ) {
		ratio = RegExp.$1 / 100;
		x = Math.floor(get_brouser_width() * ratio);
	}
	if( x > get_brouser_width() ) {
		x = Math.floor(get_brouser_width() * 0.95);
	}
	// y = eval(y)+30;
	if( !title ) title = '';
	if( !status ) status = '';
	if( !modal ) modal = true;
	if( !dialog_name ) dialog_name = 'admin_dialog';
	if( !reload ) reload = false;
	jQuery('#overlay_modal').remove();
	jQuery('#admin_dialog').remove();
	var win = new Window(dialog_name,{
		url:url,
		className: 'dialog',
		destroyOnClose: true,
		width:x,
		height:y,
		zIndex: 100000,
		resizable: true,
		minimizable: false,
		maximizable: false,
		title: title,
		recenterAuto: true,
		/*hideEffect: Effect.SwitchOff,*/
		// parent: document.getElementById('cms_contents_area'),
		draggable:true,
		wiredDrag: false,
		showEffectOptions:{duration:0.1},
		hideEffectOptions:{duration:0},
		duration:0,
		onResize:function(){
			try{
				var parent = parent;
				var p = parent.document;
			}catch(e){
				var parent = window;
			}
			if( !parent.Windows ) return;
			var winobj = parent.Windows.getFocusedWindow();
			if( winobj === null ) return;
			// ダイアログ外側のサイズ
			var size = winobj.getSize();
			// スクリーンの現在のサイズ
			var scr = screenInfomation();
			// ダイアログのインラインフレーム内コンテンツの高さ
			var h = 240;
			if(  document.body && document.body.offsetHeight ) {
				h = document.body.offsetHeight;
			} else if ( document.documentElement && document.documentElement.offsetHeight )  {
				h = document.documentElement.offsetHeight;
			}
			// ダイアログのヘッダ+フッタの高さ
			if( !!parent.$('admin_dialog_row1') && !!parent.$('admin_dialog_row3')  && !!parent.$('cms_dialog_ctrl_td') ) {
				var hof = parent.Element.getDimensions('admin_dialog_row1').height + parent.Element.getDimensions('admin_dialog_row3').height  + parent.jQuery('#cms_dialog_rowmid').height();
				//最低限のウインドウの高さのマージン（かたっぽ）
				var min_h_margin = 15;
				if( h > scr.nowHeight - hof - min_h_margin*2 || 1 ) h = scr.nowHeight - hof - min_h_margin*2 ;
				winobj.setSize(size['width'],h);
				size = winobj.getSize();
				real_height = size.height + winobj.heightS + winobj.heightN;
				x = ((scr.width/2) - size.width/2);
				y = min_h_margin;//(( scr.nowHeight - (real_height+hof) )/2 + scr.y + min_h_margin * 2);// - jQuery(window).scrollTop() ;
				winobj.showCenter(null,y,x);
			}

			$('admin_dialog_content').height = $('admin_dialog_table_content').height;
			var $iframe = jQuery($('admin_dialog_content').contentWindow.document);
			var frameHeight = jQuery('#admin_dialog_table_content').height();
			var height = frameHeight-$iframe.find('#cms_navigation_main .cms-navigation-wrap--head').height();
			$iframe.find('.cms-navigation-wrap__sub-scroll').height(height);
			var addHeight = 0;
			if($iframe.find('.cms-navigation-nav__table').length > 0 ){
				addHeight = $iframe.find('.cms-navigation-nav__table').css('padding').replace('px','') * 2;
			}
			if($iframe.find('.cms-navigation-wrap__main').length > 0){
				addHeight += $iframe.find('.cms-navigation-wrap__main').height();
			}
			if($iframe.find('#cms_navigation_main .cms-table-list--scroll').length > 0){
				addHeight += $iframe.find('#cms_navigation_main .cms-table-list--scroll').height();
			}
			var height = frameHeight - addHeight;
			$iframe.find('#cms_navigation_list').height(height);
			jQuery($('admin_dialog_content').contentWindow.document).find('#cms_dialog_container').height(jQuery('#admin_dialog_table_content').height());
			jQuery($('admin_dialog_content').contentWindow.document.html).height($('admin_dialog_table_content').height);
			jQuery($('admin_dialog_content').contentWindow.document).find('iframe').each(function(){
				if( this.id && this.parentNode.tagName != 'TD' && jQuery(this).position().top > 0) {
					jQuery(this).height(jQuery('#admin_dialog_content').height()-jQuery(this).position().top);
				}
			});
		},
		onMaximize:function(){
			// $('admin_dialog_content').height = $('admin_dialog_table_content').height;
			// jQuery($('admin_dialog_content').contentWindow.document).find('#cms_navigation_list').height(jQuery('#admin_dialog_table_content').height()-jQuery($('admin_dialog_content').contentWindow.document).find('#cms_navigation_main>.cms_list_table').height());
			// jQuery($('admin_dialog_content').contentWindow.document).find('#cms_dialog_container').height(jQuery('#admin_dialog_table_content').height());
			// jQuery($('admin_dialog_content').contentWindow.document.html).height($('admin_dialog_table_content').height);
			// jQuery($('admin_dialog_content').contentWindow.document).find('iframe').each(function(){
			// 	if( this.id && this.parentNode.tagName != 'TD' && jQuery(this).position().top > 0 ) {
			// 		jQuery(this).height(jQuery('#admin_dialog_content').height()-jQuery(this).position().top);
			// 	}
			// });
		},
		onload:function(){
			if(jQuery('#admin_dialog .dialog_close').find('svg').length == 0 ){
				var svg = '<a class="cms-dialog-top-close">'
					+'<svg class="icon--color-dark">'
					+'<use xlink:href="/_administrator/css/default/images/svg/symbol-defs.svg#icon-close"></use>'
					+'</svg></a>';
				jQuery('#admin_dialog .dialog_close').css('background','none').append(svg);
			}
			$('admin_dialog_content').height = $('admin_dialog_table_content').height;
			var $iframe = jQuery($('admin_dialog_content').contentWindow.document);
			var frameHeight = jQuery('#admin_dialog_table_content').height();
			var height = frameHeight-$iframe.find('#cms_navigation_main .cms-navigation-wrap--head').height();
			$iframe.find('.cms-navigation-wrap__sub-scroll').height(height);
			var addHeight = 0;
			if($iframe.find('.cms-navigation-nav__table').length > 0 ) addHeight = $iframe.find('.cms-navigation-nav__table').css('padding').replace('px','') * 2;
			// var height = frameHeight-$iframe.find('#cms_navigation_main>.cms-table-list').height()-$iframe.find('#cms_navigation_main .cms-navigation-wrap--head').height() - addHeight;
			// var height = frameHeight-$iframe.find('.cms-navigation-wrap__main').height()-$iframe.find('#cms_navigation_main .cms-table-list').height() - addHeight - 200;
			var addHeight = 0;
			if($iframe.find('.cms-navigation-nav__table').length > 0 ){
				addHeight = $iframe.find('.cms-navigation-nav__table').css('padding').replace('px','') * 2;
			}
			if($iframe.find('.cms-navigation-wrap__main').length > 0){
				addHeight += $iframe.find('.cms-navigation-wrap__main').height();
			}
			if($iframe.find('#cms_navigation_main .cms-table-list--scroll').length > 0){
				addHeight += $iframe.find('#cms_navigation_main .cms-table-list--scroll').height();
			}
			var height = frameHeight - addHeight;
			$iframe.find('#cms_navigation_list').height(height);
			jQuery($('admin_dialog_content').contentWindow.document).find('#cms_dialog_container').height(jQuery('#admin_dialog_table_content').height());
			jQuery($('admin_dialog_content').contentWindow.document.html).height($('admin_dialog_table_content').height);
			jQuery($('admin_dialog_content').contentWindow.document).find('iframe').each(function(){
// console.log(jQuery(this).position().top);
				if( this.id && this.parentNode.tagName != 'TD' && jQuery(this).position().top > 0) {
					jQuery(this).height(jQuery('#admin_dialog_content').height()-jQuery(this).position().top);
				}
			});
			// jQuery.get('https://manual-v3.secure-cms.net/category.php?c='+win.options.title,function(c){
			// 	if(c && jQuery('.cms-helpsite-btn').length == 0){
			// 		var html = ''
			// 		// +'<a href="#" onclick="alert(1);" class="">'
			// 		+'<a href="#" style="z-index:1000000" onclick="alert(1);/* OpenSubWin(\'/_administrator/editor/help'+c+'\', 767, 860,\'help\');*/" class="cms-helpsite-btn cms-dialog-top-help">'
			// 		// + "testwerwerwerwerwrwwe</a>";
			// 		+'<svg class="icon--color-dark" onclick="alert(2);">'
			// 		+'<use xlink:href="/_administrator/css/default/images/svg/symbol-defs.svg#icon-help"></use>'
			// 		+'</svg></a><script>alert(3);</script>';
			// 		// jQuery('#admin_dialog_top').append(html);
			// 		var a = document.createElement('span');
			// 		a.href="javascript:;";
			// 		a.className = 'cms-helpsite-btn cms-dialog-top-help';
			// 		a.onclick = function(){ OpenSubWin('/_administrator/editor/help'+c,767,860,'help'); return false; };
			// 		a.onmousedown = function(){ event.stopPropagation();};
			// 		var svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
			// 		svg.setAttribute("xmlns", "http://www.w3.org/2000/svg");
			// 		svg.setAttribute("xmlns:xlink", "http://www.w3.org/1999/xlink");
			// 		svg.setAttribute("class", "icon--color-dark");
			// 		svg.innerHTML = '<use xlink:href="/_administrator/css/default/images/svg/symbol-defs.svg#icon-help"></use>';
			// 		a.append(svg);
			// 		jQuery('#admin_dialog_top').append(a);
			// 		// jQuery('.cms-dialog-top-help').on('click', function(event) {
			// 		// 	console.log('test');
			// 		// 	OpenSubWin('/_administrator/editor/help'+c+'/', 767, 860,'help');
			// 		// 	return false;
			// 		// });
			// 	}
			// });
		}
	});
	if( status ) win.setStatusBar(status);
	if( !reload ) win.setCloseCallback(windowReload);
	if( mobile )
	{
		win.show(modal);
	} else {
		win.showCenter(modal);
	}
	// win.setURL(url);
	set_cookie(cookie_first_url, url);
}

var barid = "cms_contentparts_sidebar";
function open_side_bar(url, title, position)
{
	var sidebar = '<div id="'+barid+'"></div>';
	jQuery('html').css("overflow","hidden");
	//jQuery('body').css("overflow","hidden");
	jQuery.ajax(url,{
		type: 'get',
		dataType: 'text',
		cache: false,
		timeout: 7000
	}).done(function(data){
		//console.log(data);
		if(data == 'error')
		{
			alert_dialog('通信エラーが発生しました。再度お試しください。');
			jQuery('html').css("overflow","auto");
			context_menu.init();
			return false;
		}
		
		context_menu.clear_event();
		if(jQuery('.cms-mouseover-infobox').length != 0)
			jQuery('.cms-mouseover-infobox').remove();
		
		if(jQuery('#'+barid).length == 0)
			jQuery('body').append(sidebar);
			//jQuery('body').after(sidebar);
		jQuery('#'+barid).css({'position':'fixed','top':'0','z-index':'100001'});
		jQuery('#'+barid).css(position,'0');
		jQuery('#'+barid).html(data);
		
		if(jQuery('i.fa-times').length != 0)
		{
			jQuery('i.fa-times').on('click', function() {
				jQuery('#'+barid).remove();
				jQuery('html').css("overflow","auto");
				//jQuery('body').css("overflow","auto");
				context_menu.init();
			});
		}
	}).fail(function() {
		alert_dialog('通信エラーが発生しました。再度お試しください。');
		context_menu.init();
		return false;
	});
	set_cookie(cookie_first_url, url);
}

var reload_flag=false;
function windowReload()
{
	/*location.reload();*/
	if( reload_flag !== false )
	{
		if( reload_flag === 'ajax' )
		{
			info_dialog('更新中...', 200, 100, true);
			new Ajax.Updater(
				{success:'cms_contents_area'},
				location.href, {
					method: "get",
					parameters : 'cmsmode=reload',
					evalScripts: true,
					onFailure:function(httpObj){
						$(elm).innerHTML = "Error!!";
					},
					onSuccess:function(httpobj){
						Dialog.closeInfo();
					}
				}
			);
			reload_flag = false;
		} else if( reload_flag === true || reload_flag === 'reload' ) {
			location.reload();
		}
	}
	if( typeof context_menu == 'object' ) context_menu.init();
	return true;
}
function windowClose()
{
	return true;
}
var debug = {
	win: null,
	p: function(str){
		if( !debug.win ) {
			debug.o();
		}
		debug.win.document.write(str+"<br>");
	},
	o: function(){
		debug.win = window.open('about:blank','debug','width=300,height=300,resizable=yes');
	}
};
var target_element=null;
function showFileManager(dir, element_name){
	if( !element_name ) element_name = null;
	target_element = element_name;
	var url = "/_administrator/editor/FCKeditor/editor/filemanager/browser/mcpuk/browser.html?Type=File&Connector=connectors/php/connector.php";
	if( dir ){
		url += '&CurrentFolder=' + dir.replace(/\/+/,"/");
	} else if( get_cookie('close_file_dir') !== ''  ) {
		url += '&CurrentFolder=' + get_cookie('close_file_dir').replace(/\/+/,"/");
	}
	x=800;
	y=600;
	x = screen.width * .7;
	y = (screen.height - 50) * .8;
	OpenSubWin(url,x,y,'server_browser');
}
function showImageManager(dir, element_name){
	if( !element_name ) element_name = null;
	target_element = element_name;
	var url = "/_administrator/editor/FCKeditor/editor/filemanager/browser/mcpuk/browser.html?Type=Image&Connector=connectors/php/connector.php";
	if( dir ){
		url += '&CurrentFolder=' + dir.replace(/\/+/,"/");
	} else if( get_cookie('close_image_dir') !== ''  ) {
		url += '&CurrentFolder=' + get_cookie('close_image_dir').replace(/\/+/,"/");
	}
	x=800;
	y=600;
	x = screen.width * .7;
	y = (screen.height - 50) * .8;
	OpenSubWin(url,x,y,'server_browser');
}
function SetUrl( fileUrl ){

	if( !!target_element && !!$(target_element) ) {
		$(target_element).value = fileUrl;
		if(!!$(target_element).onchange) $(target_element).onchange();

	} else if( typeof context_menu == 'object' && !!context_menu.easy_edit_mode ) {
		context_menu.easy_edit_mode_image(fileUrl);
	} else {
		OpenSubWin(fileUrl,600,480,"image");
		return true;
	}
}
function OpenSubWin(url, x, y,winname ){
	if( !url ) return false;
	if( !winname ) winname = 'subwin';
	var option = '';
	if( !mobile )
	{
		if( !x ) x = 600;
		if( !y ) y = 480;
		wx = screen.width;
		wy = screen.height - 50;
		dx  = ( wx - x ) / 2;
		dy   = ( wy - y ) / 2;
		option  = "top=" + dy + 'px';
		option += ",left=" + dx + 'px';
		option += ",width=" + x + 'px';
		option += ",height=" + y + 'px';
		option += ",scrollbars=yes,status=yes,resizable=yes,chrome=yes,centerscreen=yes";
		w = window.open(url,winname,option);
		// w.moveTo(dx,dy);
		w.focus();
	}
	else
	{
		window.open(url,winname,option);
	}
}
function screenInfomation(){
	var s = new Object();
	var p;
	try {
		p = parent.document;
		s.width     = p.documentElement.clientWidth||p.body.clientWidth;    // 横幅
		s.nowHeight = p.documentElement.clientHeight;    // 現在表示している画面の高さ
		s.height    = p.documentElement.scrollHeight||p.body.clientHeight;    // 画面の高さ
		s.x = p.documentElement.scrollLeft||p.body.scrollLeft;    // 横の移動量
		s.y = p.documentElement.scrollTop||p.body.scrollTop;      // 縦の移動量
	} catch(e) {
		s.width     = document.body.clientWidth;
		s.nowHeight = document.body.clientHeight;
		s.height    = window.screen.height - 200;
		s.x = document.body.scrollLeft;
		s.y = document.body.scrollTop;
		p = window.document;
		s.width     = p.documentElement.clientWidth||p.body.clientWidth;    // 横幅
		s.nowHeight = p.documentElement.clientHeight;    // 現在表示している画面の高さ
		s.height    = p.documentElement.scrollHeight||p.body.clientHeight;    // 画面の高さ
		s.x = p.documentElement.scrollLeft||p.body.scrollLeft;    // 横の移動量
		s.y = p.documentElement.scrollTop||p.body.scrollTop;      // 縦の移動量


	}
	return s;
}

function get_brouser_height(){
	// IE以外。
	if (!document.all && (document.layers || document.getElementById)) {
	    return window.innerHeight;
	    }
	// ウィンドウズIE 6・標準モード。
	else if (document.getElementById && (document.compatMode=='CSS1Compat')) {
	    return document.documentElement.clientHeight;
	    }
	// その他のIE。
	else if (document.all) {
	    return document.body.clientHeight;
	    }
	// その他(非対応)。
	else {
	    return 700;
	    }
}
function get_brouser_width(){
	// IE以外。
	if (!document.all && (document.layers || document.getElementById)) {
	    return window.innerWidth;
	    }
	// ウィンドウズIE 6・標準モード。
	else if (document.getElementById && (document.compatMode=='CSS1Compat')) {
	    return document.documentElement.clientWidth;
	    }
	// その他のIE。
	else if (document.all) {
	    return document.body.clientWidth;
	    }
	// その他(非対応)。
	else {
	    return 1024;
	    }
}
function isNumeric(num){
	var numeric="0123456789";
	if(num.length==0){
		return true;
	}
	for(i=0;i < num.length;i++){
		if(numeric.indexOf(num.charAt(i))<0){
			return false;
		}
	}
	return true;
}
/**
* デバッグ用
*
**/
if (!('console' in window)) {

  window.console = {};
  window.console.log = function(str){
      return str;
  };
  window.console.warn = function(str){
      return str;
  };
  window.console.info = function(str){
      return str;
  };
  window.console.error = function(str){
      return str;
  };
}
function _uc(str) {
	return encodeURIComponent(str);
}
function _u(str) {
	return encodeURI(str);
}
function _h(str) {
	return html_escape(str);
}
function html_escape(str) {
	if(typeof str !== 'string') throw 'invalid parameter';
	return str.replace(/[&'`"<>]/g, function (match) { //'
		return {
			'&': '&amp;',
			"'": '&#x27;',
			'`': '&#x60;',
			'"': '&quot;',
			'<': '&lt;',
			'>': '&gt;'
		}[match]
	});
}

var base_url = (location.protocol=='http:')? 'https://www.akatake.co.jp':'https://www.akatake.co.jp';
var now_url = location.host.replace('www.','');
/*
if( 'https://www.akatake.co.jp'.replace('http://','').replace('www.','') !== now_url ){
	base_url = '//'+now_url;
}
*/
base_url = base_url.replace(/^https?:/,'');
/*
*/
var fileLoadingImage2 = base_url + "/_administrator/images/loading.gif";		
var fileBottomNavCloseImage2 =  base_url + "/_administrator/images/closelabel.gif";

var overlayOpacity2 = 0.8;	// controls transparency of shadow overlay

var animate2 = true;			// toggles resizing animations
var resizeSpeed2 = 7;		// controls the speed of the image resizing animations (1=slowest and 10=fastest)

var borderSize2 = 10;		//if you adjust the padding in the CSS, you will need to update this variable
var imageArray2 = new Array;
var activeImage2;

if(animate2 == true){
	overlayDuration2 = 0.2;	// shadow fade in/out duration
	if(resizeSpeed2 > 10){ resizeSpeed2 = 10;}
	if(resizeSpeed2 < 1){ resizeSpeed2 = 1;}
	resizeDuration2 = (11 - resizeSpeed2) * 0.15;
} else { 
	overlayDuration2 = 0;
	resizeDuration2 = 0;
}
Object.extend(Element, {
	getWidth: function(element) {
	   	element = $(element);
	   	return element.offsetWidth; 
	},
	setWidth: function(element,w) {
	   	element = $(element);
    	element.style.width = w +"px";
	},
	setHeight: function(element,h) {
   		element = $(element);
    	element.style.height = h +"px";
	},
	setTop: function(element,t) {
	   	element = $(element);
    	element.style.top = t +"px";
	},
	setLeft: function(element,l) {
	   	element = $(element);
    	element.style.left = l +"px";
	},
	setSrc: function(element,src) {
    	element = $(element);
    	element.src = src; 
	},
	setHref: function(element,href) {
    	element = $(element);
    	element.href = href; 
	},
	setInnerHTML: function(element,content) {
		element = $(element);
		element.innerHTML = content;
	}
});

// -----------------------------------------------------------------------------------

//
//	Extending built-in Array object
//	- array.removeDuplicates()
//	- array.empty()
//
Array.prototype.removeDuplicates = function () {
    for(i = 0; i < this.length; i++){
        for(j = this.length-1; j>i; j--){        
            if(this[i][0] == this[j][0]){
                this.splice(j,1);
            }
        }
    }
}

// -----------------------------------------------------------------------------------

Array.prototype.empty = function () {
	for(i = 0; i <= this.length; i++){
		this.shift();
	}
}

// -----------------------------------------------------------------------------------

//
//	Lightbox Class Declaration
//	- initialize()
//	- start()
//	- changeImage()
//	- resizeImageContainer()
//	- showImage()
//	- updateDetails()
//	- updateNav()
//	- enableKeyboardNav()
//	- disableKeyboardNav()
//	- keyboardNavAction()
//	- preloadNeighborImages()
//	- end()
//
//	Structuring of code inspired by Scott Upton (http://www.uptonic.com/)
//
var Lightbox2 = Class.create();

Lightbox2.prototype = {
	
	// initialize()
	// Constructor runs on completion of the DOM loading. Calls updateImageList and then
	// the function inserts html at the bottom of the page which is used to display the shadow 
	// overlay and the image container.
	//
	initialize: function() {	
		
		this.updateImageList();

		// Code inserts html at the bottom of the page that looks similar to this:
		//
		//	<div id="overlay"></div>
		//	<div id="lightbox">
		//		<div id="outerImageContainer">
		//			<div id="imageContainer">
		//				<img id="lightboxImage">
		//				<div style="" id="hoverNav">
		//					<a href="#" id="prevLink"></a>
		//					<a href="#" id="nextLink"></a>
		//				</div>
		//				<div id="loading">
		//					<a href="#" id="loadingLink">
		//						<img src="images/loading.gif">
		//					</a>
		//				</div>
		//			</div>
		//		</div>
		//		<div id="imageDataContainer">
		//			<div id="imageData">
		//				<div id="imageDetails">
		//					<span id="caption"></span>
		//					<span id="numberDisplay"></span>
		//				</div>
		//				<div id="bottomNav">
		//					<a href="#" id="bottomNavClose">
		//						<img src="images/close.gif">
		//					</a>
		//				</div>
		//			</div>
		//		</div>
		//	</div>


		var objBody = document.getElementsByTagName("body").item(0);
		
		var objOverlay = document.createElement("div");
		objOverlay.setAttribute('id','overlay2');
		objOverlay.style.display = 'none';
		objOverlay.onclick = function() { myLightbox2.end(); }
		objBody.appendChild(objOverlay);
		
		var objLightbox2 = document.createElement("div");
		objLightbox2.setAttribute('id','lightbox2');
		objLightbox2.style.display = 'none';
		objLightbox2.onclick = function(e) {	// close Lightbox is user clicks shadow overlay
			if (!e) var e = window.event;
			var clickObj = Event.element(e).id;
			if ( clickObj == 'lightbox2') {
				myLightbox2.end();
			}
		};
		objBody.appendChild(objLightbox2);
			
		var objOuterImageContainer = document.createElement("div");
		objOuterImageContainer.setAttribute('id','outerImageContainer2');
		objLightbox2.appendChild(objOuterImageContainer);

		// When Lightbox starts it will resize itself from 250 by 250 to the current image dimension.
		// If animations are turned off, it will be hidden as to prevent a flicker of a
		// white 250 by 250 box.
		if(animate2){
			Element.setWidth('outerImageContainer2', 250);
			Element.setHeight('outerImageContainer2', 250);			
		} else {
			Element.setWidth('outerImageContainer2', 1);
			Element.setHeight('outerImageContainer2', 1);			
		}

		var objImageContainer = document.createElement("div");
		objImageContainer.setAttribute('id','imageContainer2');
		objOuterImageContainer.appendChild(objImageContainer);
	
		var objLightboxImage = document.createElement("img");
		objLightboxImage.setAttribute('id','lightboxImage2');
		objImageContainer.appendChild(objLightboxImage);
	
		var objHoverNav = document.createElement("div");
		objHoverNav.setAttribute('id','hoverNav2');
		objImageContainer.appendChild(objHoverNav);
	
		var objPrevLink = document.createElement("a");
		objPrevLink.setAttribute('id','prevLink2');
		objPrevLink.setAttribute('href','#');
		objHoverNav.appendChild(objPrevLink);
		
		var objNextLink = document.createElement("a");
		objNextLink.setAttribute('id','nextLink2');
		objNextLink.setAttribute('href','#');
		objHoverNav.appendChild(objNextLink);
	
		var objLoading = document.createElement("div");
		objLoading.setAttribute('id','loading2');
		objImageContainer.appendChild(objLoading);
	
		var objLoadingLink = document.createElement("a");
		objLoadingLink.setAttribute('id','loadingLink2');
		objLoadingLink.setAttribute('href','#');
		objLoadingLink.onclick = function() { myLightbox2.end(); return false; }
		objLoading.appendChild(objLoadingLink);
	
		var objLoadingImage = document.createElement("img");
		objLoadingImage.setAttribute('src', fileLoadingImage2);
		objLoadingLink.appendChild(objLoadingImage);

		var objImageDataContainer = document.createElement("div");
		objImageDataContainer.setAttribute('id','imageDataContainer2');
		objLightbox2.appendChild(objImageDataContainer);

		var objImageData = document.createElement("div");
		objImageData.setAttribute('id','imageData2');
		objImageDataContainer.appendChild(objImageData);
	
		var objImageDetails = document.createElement("div");
		objImageDetails.setAttribute('id','imageDetails2');
		objImageData.appendChild(objImageDetails);
	
		var objCaption = document.createElement("span");
		objCaption.setAttribute('id','caption2');
		objImageDetails.appendChild(objCaption);
	
		var objNumberDisplay = document.createElement("span");
		objNumberDisplay.setAttribute('id','numberDisplay2');
		objImageDetails.appendChild(objNumberDisplay);
		
		var objBottomNav = document.createElement("div");
		objBottomNav.setAttribute('id','bottomNav2');
		objImageData.appendChild(objBottomNav);
	
		var objBottomNavCloseLink = document.createElement("a");
		objBottomNavCloseLink.setAttribute('id','bottomNavClose2');
		objBottomNavCloseLink.setAttribute('href','#');
		objBottomNavCloseLink.onclick = function() { myLightbox2.end(); return false; }
		objBottomNav.appendChild(objBottomNavCloseLink);
	
		var objBottomNavCloseImage = document.createElement("img");
		objBottomNavCloseImage.setAttribute('src', fileBottomNavCloseImage2);
		objBottomNavCloseLink.appendChild(objBottomNavCloseImage);
	},


	//
	// updateImageList()
	// Loops through anchor tags looking for 'lightbox' references and applies onclick
	// events to appropriate links. You can rerun after dynamically adding images w/ajax.
	//
	updateImageList: function() {	
		if (!document.getElementsByTagName){ return; }
		var anchors = document.getElementsByTagName('a');
		var areas = document.getElementsByTagName('area');

		// loop through all anchor tags
		for (var i=0; i<anchors.length; i++){
			var anchor = anchors[i];
			
			var relAttribute = String(anchor.getAttribute('rel'));
			
			// use the string.match() method to catch 'lightbox' references in the rel attribute
			if (anchor.getAttribute('href') && (relAttribute.toLowerCase().match('lightbox2'))){
				anchor.onclick = function () {myLightbox2.start(this); return false;}
			}
		}

		// loop through all area tags
		// todo: combine anchor & area tag loops
		for (var i=0; i< areas.length; i++){
			var area = areas[i];
			
			var relAttribute = String(area.getAttribute('rel'));
			
			// use the string.match() method to catch 'lightbox' references in the rel attribute
			if (area.getAttribute('href') && (relAttribute.toLowerCase().match('lightbox2'))){
				area.onclick = function () {myLightbox2.start(this); return false;}
			}
		}
	},
	
	
	//
	//	start()
	//	Display overlay and lightbox. If image is part of a set, add siblings to imageArray2.
	//
	start: function(imageLink) {	

		hideSelectBoxes();
		hideFlash();

		// stretch overlay to fill page and fade in
		var arrayPageSize = getPageSize();
		Element.setWidth('overlay2', arrayPageSize[0]);
		Element.setHeight('overlay2', arrayPageSize[1]);

		new Effect.Appear('overlay2', { duration: overlayDuration2, from: 0.0, to: overlayOpacity2 });

		imageArray2 = [];
		imageNum = 0;		

		if (!document.getElementsByTagName){ return; }
		var anchors = document.getElementsByTagName( imageLink.tagName);

		// if image is NOT part of a set..
		if((imageLink.getAttribute('rel') == 'lightbox2')){
			// add single image to imageArray2
			imageArray2.push(new Array(imageLink.getAttribute('href'), imageLink.getAttribute('title')));			
		} else {
		// if image is part of a set..

			// loop through anchors, find other images in set, and add them to imageArray2
			for (var i=0; i<anchors.length; i++){
				var anchor = anchors[i];
				if (anchor.getAttribute('href') && (anchor.getAttribute('rel') == imageLink.getAttribute('rel'))){
					imageArray2.push(new Array(anchor.getAttribute('href'), anchor.getAttribute('title')));
				}
			}
			imageArray2.removeDuplicates();
			while(imageArray2[imageNum][0] != imageLink.getAttribute('href')) { imageNum++;}
		}

		// calculate top and left offset for the lightbox 
		var arrayPageScroll = getPageScroll();
		var lightboxTop = arrayPageScroll[1] + (arrayPageSize[3] / 10);
		var lightboxLeft = arrayPageScroll[0];
		Element.setTop('lightbox2', lightboxTop);
		Element.setLeft('lightbox2', lightboxLeft);
		
		Element.show('lightbox2');
		
		this.changeImage(imageNum);
	},

	//
	//	changeImage()
	//	Hide most elements and preload image in preparation for resizing image container.
	//
	changeImage: function(imageNum) {	
		
		activeImage2 = imageNum;	// update global var

		// hide elements during transition
		if(animate2){ Element.show('loading2');}
		Element.hide('lightboxImage2');
		Element.hide('hoverNav2');
		Element.hide('prevLink2');
		Element.hide('nextLink2');
		Element.hide('imageDataContainer2');
		Element.hide('numberDisplay2');		
		
		imgPreloader = new Image();
		
		// once image is preloaded, resize image container
		imgPreloader.onload=function(){
			Element.setSrc('lightboxImage2', imageArray2[activeImage2][0]);
			myLightbox2.resizeImageContainer(imgPreloader.width, imgPreloader.height);
			
			imgPreloader.onload=function(){};	//	clear onLoad, IE behaves irratically with animate2d gifs otherwise 
		}
		imgPreloader.src = imageArray2[activeImage2][0];
	},

	//
	//	resizeImageContainer()
	//
	resizeImageContainer: function( imgWidth, imgHeight) {

		// get curren width and height
		this.widthCurrent = Element.getWidth('outerImageContainer2');
		this.heightCurrent = Element.getHeight('outerImageContainer2');

		// get new width and height
		var widthNew = (imgWidth  + (borderSize2 * 2));
		var heightNew = (imgHeight  + (borderSize2 * 2));

		// scalars based on change from old to new
		this.xScale = ( widthNew / this.widthCurrent) * 100;
		this.yScale = ( heightNew / this.heightCurrent) * 100;

		// calculate size difference between new and old image, and resize if necessary
		wDiff = this.widthCurrent - widthNew;
		hDiff = this.heightCurrent - heightNew;

		if(!( hDiff == 0)){ new Effect.Scale('outerImageContainer2', this.yScale, {scaleX: false, duration: resizeDuration2, queue: 'front'}); }
		if(!( wDiff == 0)){ new Effect.Scale('outerImageContainer2', this.xScale, {scaleY: false, delay: resizeDuration2, duration: resizeDuration2}); }

		// if new and old image are same size and no scaling transition is necessary, 
		// do a quick pause to prevent image flicker.
		if((hDiff == 0) && (wDiff == 0)){
			if (navigator.appVersion.indexOf("MSIE")!=-1){ pause(250); } else { pause(100);} 
		}

		Element.setHeight('prevLink2', imgHeight);
		Element.setHeight('nextLink2', imgHeight);
		Element.setWidth( 'imageDataContainer2', widthNew);

		this.showImage();
	},
	
	//
	//	showImage()
	//	Display image and begin preloading neighbors.
	//
	showImage: function(){
		Element.hide('loading2');
		new Effect.Appear('lightboxImage2', { duration: resizeDuration2, queue: 'end', afterFinish: function(){	myLightbox2.updateDetails(); } });
		this.preloadNeighborImages();
	},

	//
	//	updateDetails()
	//	Display caption, image number, and bottom nav.
	//
	updateDetails: function() {
	
		// if caption is not null
		if(imageArray2[activeImage2][1]){
			Element.show('caption2');
			Element.setInnerHTML( 'caption2', imageArray2[activeImage2][1]);
		}
		
		// if image is part of set display 'Image x of x' 
		if(imageArray2.length > 1){
			Element.show('numberDisplay2');
			Element.setInnerHTML( 'numberDisplay2', "Image " + eval(activeImage2 + 1) + " of " + imageArray2.length);
		}

		new Effect.Parallel(
			[ new Effect.SlideDown( 'imageDataContainer2', { sync: true, duration: resizeDuration2, from: 0.0, to: 1.0 }), 
			  new Effect.Appear('imageDataContainer2', { sync: true, duration: resizeDuration2 }) ], 
			{ duration: resizeDuration2, afterFinish: function() {
				// update overlay size and update nav
				var arrayPageSize = getPageSize();
				Element.setHeight('overlay2', arrayPageSize[1]);
				myLightbox2.updateNav();
				}
			} 
		);
	},

	//
	//	updateNav()
	//	Display appropriate previous and next hover navigation.
	//
	updateNav: function() {

		Element.show('hoverNav2');				

		// if not first image in set, display prev image button
		if(activeImage2 != 0){
			Element.show('prevLink2');
			document.getElementById('prevLink2').onclick = function() {
				myLightbox2.changeImage(activeImage2 - 1); return false;
			}
		}

		// if not last image in set, display next image button
		if(activeImage2 != (imageArray2.length - 1)){
			Element.show('nextLink2');
			document.getElementById('nextLink2').onclick = function() {
				myLightbox2.changeImage(activeImage2 + 1); return false;
			}
		}
		
		this.enableKeyboardNav();
	},

	//
	//	enableKeyboardNav()
	//
	enableKeyboardNav: function() {
		document.onkeydown = this.keyboardAction; 
	},

	//
	//	disableKeyboardNav()
	//
	disableKeyboardNav: function() {
		document.onkeydown = '';
	},

	//
	//	keyboardAction()
	//
	keyboardAction: function(e) {
		if (e == null) { // ie
			keycode = event.keyCode;
			escapeKey = 27;
		} else { // mozilla
			keycode = e.keyCode;
			escapeKey = e.DOM_VK_ESCAPE;
		}

		key = String.fromCharCode(keycode).toLowerCase();
		
		if((key == 'x') || (key == 'o') || (key == 'c') || (keycode == escapeKey)){	// close lightbox
			myLightbox2.end();
		} else if((key == 'p') || (keycode == 37)){	// display previous image
			if(activeImage2 != 0){
				myLightbox2.disableKeyboardNav();
				myLightbox2.changeImage(activeImage2 - 1);
			}
		} else if((key == 'n') || (keycode == 39)){	// display next image
			if(activeImage2 != (imageArray2.length - 1)){
				myLightbox2.disableKeyboardNav();
				myLightbox2.changeImage(activeImage2 + 1);
			}
		}

	},

	//
	//	preloadNeighborImages()
	//	Preload previous and next images.
	//
	preloadNeighborImages: function(){

		if((imageArray2.length - 1) > activeImage2){
			preloadNextImage = new Image();
			preloadNextImage.src = imageArray2[activeImage2 + 1][0];
		}
		if(activeImage2 > 0){
			preloadPrevImage = new Image();
			preloadPrevImage.src = imageArray2[activeImage2 - 1][0];
		}
	
	},

	//
	//	end()
	//
	end: function() {
		this.disableKeyboardNav();
		Element.hide('lightbox2');
		new Effect.Fade('overlay2', { duration: overlayDuration2});
		showSelectBoxes();
		showFlash();
	}
}

// -----------------------------------------------------------------------------------

//
// getPageScroll()
// Returns array with x,y page scroll values.
// Core code from - quirksmode.com
//
function getPageScroll(){

	var xScroll, yScroll;

	if (self.pageYOffset) {
		yScroll = self.pageYOffset;
		xScroll = self.pageXOffset;
	} else if (document.documentElement && document.documentElement.scrollTop){	 // Explorer 6 Strict
		yScroll = document.documentElement.scrollTop;
		xScroll = document.documentElement.scrollLeft;
	} else if (document.body) {// all other Explorers
		yScroll = document.body.scrollTop;
		xScroll = document.body.scrollLeft;	
	}

	arrayPageScroll = new Array(xScroll,yScroll) 
	return arrayPageScroll;
}

// -----------------------------------------------------------------------------------

//
// getPageSize()
// Returns array with page width, height and window width, height
// Core code from - quirksmode.com
// Edit for Firefox by pHaez
//
function getPageSize(){
	
	var xScroll, yScroll;
	
	if (window.innerHeight && window.scrollMaxY) {	
		xScroll = window.innerWidth + window.scrollMaxX;
		yScroll = window.innerHeight + window.scrollMaxY;
	} else if (document.body.scrollHeight > document.body.offsetHeight){ // all but Explorer Mac
		xScroll = document.body.scrollWidth;
		yScroll = document.body.scrollHeight;
	} else { // Explorer Mac...would also work in Explorer 6 Strict, Mozilla and Safari
		xScroll = document.body.offsetWidth;
		yScroll = document.body.offsetHeight;
	}
	
	var windowWidth, windowHeight;
	
//	console.log(self.innerWidth);
//	console.log(document.documentElement.clientWidth);

	if (self.innerHeight) {	// all except Explorer
		if(document.documentElement.clientWidth){
			windowWidth = document.documentElement.clientWidth; 
		} else {
			windowWidth = self.innerWidth;
		}
		windowHeight = self.innerHeight;
	} else if (document.documentElement && document.documentElement.clientHeight) { // Explorer 6 Strict Mode
		windowWidth = document.documentElement.clientWidth;
		windowHeight = document.documentElement.clientHeight;
	} else if (document.body) { // other Explorers
		windowWidth = document.body.clientWidth;
		windowHeight = document.body.clientHeight;
	}	
	
	// for small pages with total height less then height of the viewport
	if(yScroll < windowHeight){
		pageHeight = windowHeight;
	} else { 
		pageHeight = yScroll;
	}

//	console.log("xScroll " + xScroll)
//	console.log("windowWidth " + windowWidth)

	// for small pages with total width less then width of the viewport
	if(xScroll < windowWidth){	
		pageWidth = xScroll;		
	} else {
		pageWidth = windowWidth;
	}
//	console.log("pageWidth " + pageWidth)

	arrayPageSize = new Array(pageWidth,pageHeight,windowWidth,windowHeight) 
	return arrayPageSize;
}

// -----------------------------------------------------------------------------------

//
// getKey(key)
// Gets keycode. If 'x' is pressed then it hides the lightbox.
//
function getKey(e){
	if (e == null) { // ie
		keycode = event.keyCode;
	} else { // mozilla
		keycode = e.which;
	}
	key = String.fromCharCode(keycode).toLowerCase();
	
	if(key == 'x'){
	}
}

// -----------------------------------------------------------------------------------

//
// listenKey()
//
function listenKey () {	document.onkeypress = getKey; }
	
// ---------------------------------------------------

function showSelectBoxes(){
	var selects = document.getElementsByTagName("select");
	for (i = 0; i != selects.length; i++) {
		selects[i].style.visibility = "visible";
	}
}

// ---------------------------------------------------

function hideSelectBoxes(){
	var selects = document.getElementsByTagName("select");
	for (i = 0; i != selects.length; i++) {
		selects[i].style.visibility = "hidden";
	}
}

// ---------------------------------------------------

function showFlash(){
	var flashObjects = document.getElementsByTagName("object");
	for (i = 0; i < flashObjects.length; i++) {
		flashObjects[i].style.visibility = "visible";
	}

	var flashEmbeds = document.getElementsByTagName("embed");
	for (i = 0; i < flashEmbeds.length; i++) {
		flashEmbeds[i].style.visibility = "visible";
	}
}

// ---------------------------------------------------

function hideFlash(){
	var flashObjects = document.getElementsByTagName("object");
	for (i = 0; i < flashObjects.length; i++) {
		flashObjects[i].style.visibility = "hidden";
	}

	var flashEmbeds = document.getElementsByTagName("embed");
	for (i = 0; i < flashEmbeds.length; i++) {
		flashEmbeds[i].style.visibility = "hidden";
	}

}


// ---------------------------------------------------

//
// pause(numberMillis)
// Pauses code execution for specified time. Uses busy code, not good.
// Help from Ran Bar-On [ran2103@gmail.com]
//

function pause(ms){
	var date = new Date();
	curDate = null;
	do{var curDate = new Date();}
	while( curDate - date < ms);
}
/*
function pause(numberMillis) {
	var curently = new Date().getTime() + sender;
	while (new Date().getTime();	
}
*/
// ---------------------------------------------------



function initLightbox2() { myLightbox2 = new Lightbox2(); }
Event.observe(window, 'load', initLightbox2, false);;(function($){
    $(window).on('load', function(event) {
        const ua = navigator.userAgent;
        if(ua.indexOf('Trident') != -1 || ua.indexOf('MSIE') != -1) {
            var script = document.createElement('script');
            script.src = "https://polyfill.io/v2/polyfill.min.js?features=IntersectionObserver";
            document.head.appendChild(script);
            $('.cparts-animate.box > div,.cparts-animate .box > div').css('opacity',1).css('transform','translate(0,0)');
            return false;
        } else {
            const options = {
                threshold: 0.1
            };
            const observer = new IntersectionObserver(function(entries) {
                for(let i in entries) {
                    let e = entries[i];
                    let target=null;
                    const appClass='moved';
                    if(e.intersectionRatio > 0 && !$(e.target).hasClass(appClass)) {
                        if( $(e.target).find('.box > div').length > 0 ) {
                            target = $(e.target).find('.box > div');
                        } else if( $(e.target).find('> div').length > 0 ) {
                            target = $(e.target).find('> div');
                        }
                        target.css('opacity',1).css('transform','none');
                        $(e.target).addClass(appClass);
                    }
                }
            },options);
            let elms = document.querySelectorAll('.cparts-animate');
            for(let i in elms) {
                if(elms.hasOwnProperty(i)) {
                    observer.observe(elms[i]);
                }
            }
        }
    });
}(jQuery));
