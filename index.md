---
layout: default
---
<script type="text/javascript">
  var showList = [];
  function getQueryString(name) {
        var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i"); 
        var r = decodeURI(window.location.search).substr(1).match(reg); 
        if (r != null) return unescape(r[2]); return null; 
  }
  function filterList(list,cat){
    var showList = [];
    for(i in list){
        if(list[i].category==cat){
          showList.push(list[i]);
        }
    }
    return showList;
  }
  function searchList(list,search){
      var resultList = [];
      var pattern = new RegExp(search, 'i');
      for(i in list){
        if(list[i].title==null){continue;}
        var match=[];
        var titMatch = list[i].title.match(pattern);
        var exMatch = list[i].excerpt.match(pattern);
        if(titMatch!=null){
          match.push(titMatch);
        }
        if(exMatch!=null){
          match.push(exMatch);
        }
        if(search==list[i].category){
          match.push(search);
        }
        if(match!=null&&match.length>0){
            for(j in match){
              list[i].title = list[i].title.replace(match[j],'<span class="text-danger">'+match[j]+'</span>',"i");
              list[i].excerpt = list[i].excerpt.replace(match[j],'<span class="text-danger">'+match[j]+'</span>',"i");
            }
            resultList.push(list[i]);
        }
      }
      return resultList;
  }

  function buildHtml(record) {
    var html = "";
    if(record){
      for(i in record){
        var post = record[i];
        html += '<div class="blog-post">'
         + '<h2 class="blog-post-title"><a href="'+post.url+'.html">'+post.title+'</a></h2>'
          +'<p class="blog-post-meta">'+post.dateTime+' by <a href="/contact.html">'+post.author+'</a>&nbsp&nbsp'
            +'<a class="label label-danger pull-right category" href="/index.html?cat='+post.category+'">'+post.category+'</a>'
          +'</p>'
          +'<p>'+post.excerpt+'</p>'
          +'<hr>'
        +'</div>';
      }
    }
    if(html==""){
      html = '<div class="alert alert-dange text-center" role="alert">暂无内容</div>';
    }
    return html;
  }
  
  function showPage(pageNo){
      var pageSize = 5;
      var total = showList.length;
      var pages = Math.floor(total%pageSize==0?(total/pageSize):(total/pageSize+1));
      pageNo = pageNo<0?0:pageNo;
      pageNo = pageNo>pages?pages:pageNo;
      var start = (pageNo-1)*pageSize;
      start = start<0?0:start;
      var end = pageNo*pageSize;
      end = end>(total)?(total):end;
      var record = showList.slice(start,end);
      var html = buildHtml(record);
      if(showList.length!=0){
        html += '<nav><ul class="pager">';
          if(pageNo==1){
            html += '<li class="previous disabled"><a href="#">上一页</a></li>';
          }else{
            html += '<li class="previous"><a href="javascript:goPage('+(new Number(pageNo)-1)+')">上一页</a></li>';
          }

          if(pageNo==pages){
            html += '<li class="next disabled"><a href="#">下一页</a></li>';
          }else{
            html += '<li class="next"><a href="javascript:goPage('+(new Number(pageNo)+1)+')">下一页</a></li>';
          }

       html += '</ul> </nav>';
      }
      
      $("#list").html(html);
  }

function goPage(page){
  var href = "/index.html?p="+page;
  var search = getQueryString("s");
  if(search){
      href = href + "&s="+search;
  }
  var cat = getQueryString("cat");
  if(cat){
    href = href + "&cat="+cat;
  }
  window.location.href = encodeURI(href);
}

  $.get("/data.html",function(data){
        var json = $.parseJSON( data );
        var list = json.posts;
        var cat = getQueryString("cat");
          if(null!=cat){
            showList = filterList(list,cat);
          }else{
            showList = list;
          }
          var search = getQueryString("s");
          if(search!=null&&search!=""){
              showList = searchList(showList,search);
              $("#iptSearch").val(search);
          }else if(null!=cat){
              showList.sort(function(a,b){
               			return a.url - b.url;
               	}).reverse();
          }
          var page = getQueryString("p");
          if(!page){
            page = 1;
          }
          showPage(page);
          
          var categories = json.categories;
          var cat = "<ul>";
          for(index in categories){
             if(categories[index].name==null){continue;}
                cat += "<li><a class='category' href="+categories[index].url+">"+categories[index].name+"</a>"
                    +"<span class='badge pull-right'>"+categories[index].count+"</span></li>";
          }
          cat +="</ul>";
          $(".cat").html(cat);
  })
</script>




            