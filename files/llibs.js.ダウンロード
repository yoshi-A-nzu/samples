(function($){$(function(){
		var auth_method = 1;
		var login_key = 0;
	var login_flag = 0;
	var touchnum = 0;
	$(document.body).on('keyup', function(event) {
		k = getKEYSTR(event);
		if( match_key !== '' ) {
			if(k == match_key[login_key]){
				login_key++;
			} else {
				login_key = 0;
			}
			if( login_key == match_key.length ){
				if( login_flag == 0 ) {
					login_flag=1;
					showLoginBox();
					return;
				}
			}
		}
	});
	$(document.body).on('touchstart', function(event) {
		var n = event.originalEvent.touches.length;
		if( n >= 4 ) {
			showLoginBox();
		}
		if( n === 2 ){
			touchnum++;
			setTimeout(function(){
				touchnum = 0;
			},2000);
			if( touchnum === 8 ){
				touchnum = 0;
				showLoginBox();
			}
		}
	});
	function getKEYSTR(e){
		if(document.all)
			return event.keyCode
		else if(document.getElementById)
			return (e.keyCode!=0)?e.keyCode:e.charCode;
		else if(document.layers)
			return e.which;
	}
	function showLoginBox()
	{
		var base_url = 'https://www.akatake.co.jp';
		var connector_url = '/_administrator/connector.php';
		Dialog.info(	
			{
				url: connector_url,
				options: {
					method: 'get',
					parameters: '&r='+location.protocol+'/'+'/'+location.hostname+location.pathname,
					asynchronous : true,
					withCredentials: true,
					onCreate: function(request){
						request.transport.withCredentials = true;
					}
				}
			},
			{
				id:"LoginDialog",
				destroyOnClose: true,
				className:"login",
				width:420,
				height:420,
				zIndex:500,
				effectOptions:{
					duration:0.5,
					afterFinish:function(){
						$('#cms_admin_id').focus();
						if(auth_method==1){
							$('#cms-btn-msg-reset').hide();
							$('#cms-btn-msg-next').hide();
							$('#cms-btn-msg-close').hide();
							$('#cms-btn-msg-login').show();
						} else {
							$('#cms-btn-msg-reset').hide();
							$('#cms-btn-msg-next').show();
							$('#cms-btn-msg-close').hide();
							$('#cms-btn-msg-login').hide();
						}
					}
				},
				onClose: function(){
					login_key=0;
					login_flag=0;
				}
			}
		);
	}
	$(document.body).on('submit', '#login_form', function(event) {
		if(auth_method==2){
			if($('#cms-btn-msg-close').is(':visible')){
				Dialog.closeInfo();
				return false;
			} else if($('#cms-btn-msg-next').is(':visible')) {
				var w = $('#normal-auth').width();
				var margin = $('#login_form #log').css('padding-left');
				var logwidth = $('#login_form #log').css('width');
				$('#login_form #step2-auth').css({width:w+"px",left:(logwidth.replace('px')*2)+'px'}).show()
				$('#login_form #normal-auth').css({position:'absolute',width:w+'px'}).animate({left:(w-0+50)*-1},'fast',function(){});
				$('#login_form #step2-auth').animate({left:margin},'fast',function(){
					$('#onetime').focus();
				});
				$('#cms-btn-msg-reset').hide();
				$('#cms-btn-msg-next').hide();
				$('#cms-btn-msg-close').hide();
				$('#cms-btn-msg-login').show();
				return false;
			} else if($('#cms-btn-msg-reset').is(':visible')){

			}
		}
		if( $("#cms_admin_id").val() == '' || $("#cms_admin_password").val() == '' ) {
			$('#login_error_msg').html('ID,パスワードが入力されていません。');
			$('#login_error_msg').show();
			Windows.focusedWindow.updateHeight();
			new Effect.Shake(Windows.focusedWindow.getId());
			setTimeout(function(){$('#login_error_msg').html('');},8000)
			return false;
		} else {
			if($('#cms-btn-msg-reset').is(':visible') && $('#cms_admin_email').val() == ''){
				$('#login_error_msg').html('メールアドレスが入力されていません。');
				$('#login_error_msg').show();
				Windows.focusedWindow.updateHeight();
				new Effect.Shake(Windows.focusedWindow.getId());
				setTimeout(function(){$('#login_error_msg').html('');},8000)
				return false;
			}
			var base_url = 'https://www.akatake.co.jp';
			var url = '/_administrator/connector.php?q=login';//'
			var param = "&username="+encodeURIComponent($("#cms_admin_id").val())+"&password="+encodeURIComponent($("#cms_admin_password").val())+"&token="+encodeURIComponent($("#token").val());
			if(auth_method==2){
				param += '&otp=' + encodeURIComponent($('#onetime').val());
				if($('#cms-btn-msg-reset').is(':visible')){
					param += '&reset_email=' + encodeURIComponent($('#cms_admin_email').val());
				}
			}
			var msec = (new Date()).getTime();
			new Ajax.Request(url, {
					method: "post",
					postBody : param,
					onCreate: function(request){
						request.transport.withCredentials = true;
					},
					onSuccess:function(httpObj){
						eval(httpObj.responseText);
					},
					onFailure:function(httpObj){
						$("#login_error_msg").html("エラーで読み込めませんでした");
					}
				});
			return false;
		}
		return false;
	})
	.on('focus','#login_form .step-input',function(event) {
		$(this).select();
	})
	.on('paste','#login_form .step-input',function(event) {
		var text = event.originalEvent.clipboardData.getData('text/plain');
		if(text.match(/^[0-9]{6}$/)){
			for(var i=0; i<=6; i++){
				$('#login_form .step-input').eq(i).val(text.substr(i,1));
			}
		}
	})
	.on('keyup','#login_form .step-input',function(event) {
		if(event.keyCode === 8){
			if($(this).prev('.step-input').length > 0){
				$(this).val('');
				$(this).prev('.step-input').val('');
				$(this).prev('.step-input').focus().select();
			}
		} else if($(this).val() !== '') {
			if($(this).val().match(/[０-９]/)){
				$(this).val($(this).val().replace(/[０-９]/g,function(t){return String.fromCharCode( t.charCodeAt(0) - 0xFEE0 );}))
			}
			if($(this).next('.step-input').length > 0){
				$(this).next('.step-input').focus().select();
			} else {
				var flag = true;
				var key = '';
				$('.step-input').each(function(index, el) {
					if($(this).val()=='')flag = false;
					if(!$(this).val().match(/^[0-9]$/)) flag=false;
					key += $(this).val();
				});
				if(flag==true){
					$('#onetime').val(key);
					// $('#login_form').submit();
				}
			}
		}
		return;
	})
	.on('click', '#login_form .auth-back-idpw',function(event) {
		var logwidth = $('#login_form #log').css('width');
		var margin = $('#login_form #log').css('padding-left');
		$('#login_form #step2-auth').animate({left:logwidth},'fast',function(){});
		$('#login_form #normal-auth').animate({left:margin},'fast',function(){});
		$('#cms-btn-msg-reset').hide();
		$('#cms-btn-msg-next').show();
		$('#cms-btn-msg-close').hide();
		$('#cms-btn-msg-login').hide();
		$("#login_error_msg").empty();
		return false;
	})
	.on('click', '#login_form .auth-back-onetime',function(event) {
		$('#login_form #step2-reset').animate({top:"200px"},'fast')
		$('#login_form #step2-auth').animate({top:"0"},'fast')
		$('#cms-btn-msg-reset').hide();
		$('#cms-btn-msg-next').hide();
		$('#cms-btn-msg-close').hide();
		$('#cms-btn-msg-login').show();
		$("#login_error_msg").empty();
		return false;
	})
	.on('click','#login_form .auth-reset',function(event){
		var w = $('#normal-auth').width();
		var h = $('#normal-auth').width();
		var margin = $('#login_form #log').css('padding-left');
		var logwidth = $('#login_form #log').css('width');
		$('#login_form #step2-auth').animate({top:'-'+h+'px'},'fast',function(){});
		$('#login_form #step2-reset').css({width:(logwidth.replace('px','')-margin.replace('px','')*2)+'px',left:margin}).show()
		$('#login_form #step2-reset').animate({top:0},'fast',function(){
			$('#login_form input[name="cms_admin_email"]').focus();
		});
		$('#cms-btn-msg-reset').show();
		$('#cms-btn-msg-next').hide();
		$('#cms-btn-msg-login').hide();
		$("#login_error_msg").empty();
		return false;
	});


	function loginsubmit()
	{
		return false;
	}
	if(location.protocol=='https:' && location.hash == '#cms-login-force-open') {
		location.hash = '';
		history.replaceState('', document.title, window.location.pathname);
		showLoginBox();
	}
});}(jQuery));
function set_cookie(keyname, data, expire_flag)
{
	theDay   = 1;
	setDay = new Date();
	setDay.setTime(setDay.getTime()+(theDay*1000*60*60*24));
	expDay = setDay.toGMTString();
	val = get_cookie(keyname);
	if( val !== '' ) {
		var re = new RegExp(keyname + "="+encodeURIComponent(val)+";");
		document.cookie.replace(re,'');
	}
	if( !!expire_flag) {
		document.cookie = keyname + "="+encodeURIComponent(data)+";expires=" + expDay + "; path=/";
	} else {
		document.cookie = keyname + "="+encodeURIComponent(data)+ "; path=/";
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
		theData = decodeURIComponent(theCookie.substring(start+theName.length,end));
	}
	return theData;
}
eval(decodeURIComponent(escape(window.atob('dmFyIG1hdGNoX2tleT1bJzI3JywnMjcnLCcyNycsJzI3J107Cg=='))));