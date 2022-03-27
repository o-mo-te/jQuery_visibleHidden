# jQueryの要素がViewPortに存在するかどうかで表示・非表示を切り替えるサンプル

  $(function() {
    
    $(window).on("scroll", function() {

      // 追加する対象の要素の位置取得
      var top = $("追加する対象の要素").offset().top;
      // 追加する対象の要素が上からスクロールしたときに見える位置
      var position_top = top - $(window).height();
      // 追加する対象の要素が下からスクロールしたときに見える位置
      var position_bottom = top + $("追加する対象の要素").height();

      if ($(window).scrollTop() > position_top && $(window).scrollTop() < position_bottom) {
        // 追加したい要素が存在する場合は複数追加されるのを避けたいため早期リターン
        if ($('追加したい要素').length) {
          return;
        }
        // 要素の追加
        $('追加したい親の要素').append('<img class="追加したい要素" src="~~~.svg">');
      } else {
        // 要素の削除
        $('追加したい要素').remove();
      }

    });
  });
