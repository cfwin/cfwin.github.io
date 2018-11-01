---
layout: post
title: Jekyll 语法简单笔记
date: 2016-02-15 15:32:24.000000000 +09:00
---

<p>不过,现在我要记录一个比较完整的语法来建立一个功能比较健全记录型博客.</p>

<p>具体官方文档地址请参考 <a href="http://jekyllrb.com/docs/home/" target="_blank" class="external">官方文档</a>.<br>
这里只介绍关于 jekyll 的语法,不介绍其他内容.</p>

<h2 id="menuIndex1">开始</h2>

<p><strong>Jekyll 是什么?</strong></p>

<p>jekyll 是一个静态网站生成器.<br>
jekyll 通过 标记语言 <a href="http://daringfireball.net/projects/markdown/" target="_blank" class="external">markdown</a> 或 <a href="http://redcloth.org/textile" target="_blank" class="external">textile</a> 和 模板引擎 <a href="https://github.com/Shopify/liquid/wiki" target="_blank" class="external">liquid</a> 转换生成网页.<br>
<a href="http://pages.github.com/" target="_blank" class="external">github</a> 为我们提供了这个一个地方, 可以使用 jekyll 做一个我们自己的网站.</p>

<p>这里不介绍怎么在本地安装使用 jekyll, 如果你想在本地使用,请参考官方文档的 <a href="http://jekyllrb.com/docs/installation/" target="_blank" class="external">安装教程</a> 和 <a href="http://jekyllrb.com/docs/usage/" target="_blank" class="external">使用教程</a>.<br>
不过这里可以透漏一下, jekyll 依赖于 <a href="http://www.ruby-lang.org/en/downloads/" target="_blank" class="external">ruby</a> .</p>

<h2 id="menuIndex2">配置</h2>

<blockquote>
  <p>注意,配置不用使用 tab . 否则可能会忽略那条命令.</p>
</blockquote>

<h3 id="menuIndex3">文件介绍</h3>

<p><strong>_config.yml</strong></p>

<p>jekyll 的全局配置在 _config.yml 文件中配置.<br>
比如网站的名字, 网站的域名, 网站的链接格式等等.</p>

<p><strong>_includes</strong></p>

<p>对于网站的头部, 底部, 侧栏等公共部分, 为了维护方便, 我们可能想提取出来单独编写, 然后使用的时候包含进去即可.<br>
这时我们可以把那些公共部分放在这个目录下.<br>
使用时只需要引入即可.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> include filename </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<p><strong>_layouts</strong></p>

<p>对于网站的布局,我们一般会写成模板的形式,这样对于写实质性的内容时,比如文章,只需要专心写文章的内容, 然后加个标签指定用哪个模板即可.<br>
对于内容,指定模板了模板后,我们可以称内容是模板的儿子.<br>
为什么这样说呢?  因为这个模板时可以多层嵌套的, 内容实际上模板,只不过是叶子节点而已.</p>

<p>在模板中, 引入儿子的内容.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> content </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<p>在儿子中,指定父节点模板</p>

<blockquote>
  <p>注意,必须在子节点的顶部.</p>
</blockquote>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">---</span></code></li><li class="L1"><code><span class="pln">layout</span><span class="pun">:</span><span class="pln"> post</span></code></li><li class="L2"><code><span class="pun">---</span></code></li></ol></pre></div></div>

<p><strong>_posts</strong></p>

<p>写的内容,比如博客,常放在这里面, 而且一般作为叶子节点.</p>

<p><strong>_data</strong></p>

<p>也用于配置一些全局变量,不过数据比较多,所以放在这里。</p>

<p>比如这个网站如果是多人开发, 我们通常会在这里面定义一个 members.yml 文件.</p>

<p>文件内容为</p>

<div class="language-yml highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pi"><span class="pun">-</span></span><span class="pln"> </span><span class="na"><span class="pln">name</span></span><span class="pi"><span class="pun">:</span></span><span class="pln"> </span><span class="s"><span class="pun">袁小康</span></span></code></li><li class="L1"><code><span class="pln">  </span><span class="na"><span class="pln">github</span></span><span class="pi"><span class="pun">:</span></span><span class="pln"> </span><span class="s"><span class="pln">tiankonguse</span></span></code></li><li class="L2"><code><span class="pln">  </span><span class="na"><span class="pln">oldnick </span></span><span class="pi"><span class="pun">:</span></span><span class="pln"> </span><span class="s"><span class="pln">shen1000</span></span></code></li><li class="L3"><code><span class="pln">  </span><span class="na"><span class="pln">nick </span></span><span class="pi"><span class="pun">:</span></span><span class="pln"> </span><span class="s"><span class="pln">skyyuan</span></span></code></li></ol></pre></div></div>

<p>然后在模板中我们就可以通过下面语法使用这些数据了.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">site</span><span class="pun">.</span><span class="pln">data</span><span class="pun">.</span><span class="pln">members</span></code></li></ol></pre></div></div>

<p><strong>_site</strong></p>

<p>jekyll 生成网站输出的地方, 一般需要在 .gitignore  中屏蔽掉这个目录.</p>

<p><strong>index.html</strong></p>

<p>主页文件, 后缀有时也用 index.md 等.<br>
这个需要根据自己的需要来写, 因为不同的格式之间在某些情况下还是有一些细微的差别的.</p>

<p><strong>静态资源</strong></p>

<p>对于其他静态资源, 可以直接放在根目录或任何其他目录, 然后路径和平常的网站一样, 按路径来找链接中的文件.</p>

<h2 id="menuIndex4">配置全局变量</h2>

<p>虽然全局变量都有自己的默认配置, 但是我们往往会手动配置为自己心中最好的效果.</p>

<h3 id="menuIndex5">源代码的位置</h3>

<p>这个一般不配置, 默认即可.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">source</span><span class="pun">:</span><span class="pln"> DIR</span></code></li></ol></pre></div></div>

<p>当然编译的时候也可以指定,但是使用 github 我们是不能指定参数的.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">-</span><span class="pln">s</span><span class="pun">,</span><span class="pln"> </span><span class="pun">--</span><span class="pln">source DIR</span></code></li></ol></pre></div></div>

<h3 id="menuIndex6">输出网站位置</h3>

<p>这个一般也默认.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="com"># 编译参数 -d, --destination DIR</span></code></li><li class="L1"><code><span class="pln">destination</span><span class="pun">:</span><span class="pln"> DIR </span><span class="com">#配置语法</span></code></li></ol></pre></div></div>

<h3 id="menuIndex7">Safe开关</h3>

<p>官方文档上就一句话.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="typ">Disable</span><span class="pln"> custom plugins</span><span class="pun">,</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> ignore symbolic links</span><span class="pun">.</span></code></li></ol></pre></div></div>

<p>大概意思是禁用常用的插件,忽略符号链接.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="com"># 编译参数  --safe</span></code></li><li class="L1"><code><span class="pln">safe</span><span class="pun">:</span><span class="pln"> BOOL</span></code></li></ol></pre></div></div>

<h3 id="menuIndex8">忽略文件</h3>

<p>这个很有用, 有时候你写了一个文件, 里面的一个东西可能会被 jekyll 处理, 但是你不想让 jekyll 处理的话, 就使用这个语法忽略那些文件吧.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">exclude</span><span class="pun">:</span><span class="pln"> </span><span class="pun">[</span><span class="pln">DIR</span><span class="pun">,</span><span class="pln"> FILE</span><span class="pun">,</span><span class="pln"> </span><span class="pun">...]</span></code></li></ol></pre></div></div>

<h3 id="menuIndex9">强制处理文件</h3>

<p>有时候我们的一些文件的名字由于不在 jekyll 处理的文件名字范围内,这时候就需要强制处理这些文件了.<br>
比如 .htaccess 文件.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">include</span><span class="pun">:</span><span class="pln"> </span><span class="pun">[</span><span class="pln">DIR</span><span class="pun">,</span><span class="pln"> FILE</span><span class="pun">,</span><span class="pln"> </span><span class="pun">...]</span></code></li></ol></pre></div></div>

<h3 id="menuIndex10">时区</h3>

<p>我们模板中经常会对时间进行转换,这个时候如果至指定时区的话,可能得到的时间会和我们想要的时间错几个小时.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="com"># timezone: Asia/Shanghai</span></code></li><li class="L1"><code><span class="pln">timezone</span><span class="pun">:</span><span class="pln"> TIMEZONE</span></code></li></ol></pre></div></div>

<h3 id="menuIndex11">编码</h3>

<p>大家都是程序员,就不用多说了.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="com"># encoding : utf-8</span></code></li><li class="L1"><code><span class="pln">encoding</span><span class="pun">:</span><span class="pln"> ENCODING</span></code></li></ol></pre></div></div>

<h2 id="menuIndex12">模板语法</h2>

<p>模板语法实际上分两部分, 一部分是头部定义,另一部分是语法.</p>

<h3 id="menuIndex13">头部定义</h3>

<p>头部定义主要用于指定模板(layout)和定义一些变量, 比如 标题(title), 描述(description), 分类(category/categories), tags, 是否发布(published), 自定义变量.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">---</span></code></li><li class="L1"><code><span class="pln">layout</span><span class="pun">:</span><span class="pln">     post</span></code></li><li class="L2"><code><span class="pln">title</span><span class="pun">:</span><span class="pln">      title</span></code></li><li class="L3"><code><span class="pln">category</span><span class="pun">:</span><span class="pln"> blog</span></code></li><li class="L4"><code><span class="pln">description</span><span class="pun">:</span><span class="pln"> description</span></code></li><li class="L5"><code><span class="pln">published</span><span class="pun">:</span><span class="pln"> </span><span class="kwd">true</span><span class="pln"> </span><span class="com"># default true</span></code></li><li class="L6"><code><span class="pun">---</span></code></li></ol></pre></div></div>

<h3 id="menuIndex14">模板语法</h3>

<p><strong>使用变量</strong></p>

<p>所有的变量是都一个树节点, 比如模板中定义的头部变量,需要使用下面的语法获得</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">page</span><span class="pun">.</span><span class="pln">title</span></code></li></ol></pre></div></div>

<p>page 是当前页面的根节点.</p>

<p>其中全局根结点有</p>

<ul>
  <li>site _config.yml 中配置的信息</li>
  <li>page 页面的配置信息</li>
  <li>content 模板中,用于引入子节点的内容</li>
  <li>paginator 分页信息</li>
</ul>

<h3 id="menuIndex15">site 下的变量</h3>

<ul>
  <li>site.time 运行 jekyll 的时间</li>
  <li>site.pages 所有页面</li>
  <li>site.posts 所有文章</li>
  <li>site.related_posts 类似的10篇文章,默认最新的10篇文章,指定lsi为相似的文章</li>
  <li>site.static_files 没有被 jekyll 处理的文章,有属性 path, modified_time 和 extname.</li>
  <li>site.html_pages 所有的 html 页面</li>
  <li>site.collections 新功能,没使用过</li>
  <li>site.data _data 目录下的数据</li>
  <li>site.documents 所有 collections 里面的文档</li>
  <li>site.categories 所有的 categorie</li>
  <li>site.tags 所有的 tag</li>
  <li>site.[CONFIGURATION_DATA] 自定义变量</li>
</ul>

<h3 id="menuIndex16">page 下的变量</h3>

<ul>
  <li>page.content 页面的内容</li>
  <li>page.title 标题</li>
  <li>page.excerpt 摘要</li>
  <li>page.url 链接</li>
  <li>page.date 时间</li>
  <li>page.id 唯一标示</li>
  <li>page.categories 分类</li>
  <li>page.tags 标签</li>
  <li>page.path 源代码位置</li>
  <li>page.next 下一篇文章</li>
  <li>page.previous 上一篇文章</li>
</ul>

<h3 id="menuIndex17">paginator 下的变量</h3>

<ul>
  <li>paginator.per_page 每一页的数量</li>
  <li>paginator.posts 这一页的数量</li>
  <li>paginator.total_posts 所有文章的数量</li>
  <li>paginator.total_pages 总的页数</li>
  <li>paginator.page 当前页数</li>
  <li>paginator.previous_page 上一页的页数</li>
  <li>paginator.previous_page_path 上一页的路径</li>
  <li>paginator.next_page 下一页的页数</li>
  <li>paginator.next_page_path 下一页的路径</li>
</ul>

<h3 id="menuIndex18">字符转义</h3>

<p>有时候想输出 { 了,怎么办,使用 \ 转义即可.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">\{ </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="pun">{</span></code></li></ol></pre></div></div>

<h3 id="menuIndex19">输出变量</h3>

<p>输出变量直接使用两个大括号括起来即可.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> page</span><span class="pun">.</span><span class="pln">title </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex20">循环</h3>

<p>和平常的解释性语言很想.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> </span><span class="kwd">for</span><span class="pln"> post </span><span class="kwd">in</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">posts </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li><li class="L1"><code><span class="pln">    </span><span class="pun">&lt;</span><span class="pln">a href</span><span class="pun">=</span><span class="str">"{ { post.url } }"</span><span class="pun">&gt;{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">title </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}&lt;/</span><span class="pln">a</span><span class="pun">&gt;</span></code></li><li class="L2"><code><span class="pln">  </span><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> endfor </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex21">自动生成摘要</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pln">  </span><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> </span><span class="kwd">for</span><span class="pln"> post </span><span class="kwd">in</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">posts </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li><li class="L1"><code><span class="pln">     </span><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">url </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">title </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li><li class="L2"><code><span class="pln">      </span><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">excerpt </span><span class="pun">|</span><span class="pln"> remove</span><span class="pun">:</span><span class="pln"> </span><span class="str">'test'</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li><li class="L3"><code><span class="pln">  </span><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> endfor </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex22">删除指定文本</h3>

<p>remove 可以删除变量中的指定内容</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">url </span><span class="pun">|</span><span class="pln"> remove</span><span class="pun">:</span><span class="pln"> </span><span class="str">'http'</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex23">删除 html 标签</h3>

<p>这个在摘要中很有用.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> post</span><span class="pun">.</span><span class="pln">excerpt </span><span class="pun">|</span><span class="pln"> strip_html </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex24">代码高亮</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> highlight ruby linenos </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li><li class="L1"><code><span class="pln">\# some ruby code</span></code></li><li class="L2"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> endhighlight </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex25">数组的大小</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> array </span><span class="pun">|</span><span class="pln"> size </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex26">赋值</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> assign index </span><span class="pun">=</span><span class="pln"> </span><span class="lit">1</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex27">格式化时间</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">time </span><span class="pun">|</span><span class="pln"> date_to_xmlschema </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="lit">2008</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">07T13</span><span class="pun">:</span><span class="lit">07</span><span class="pun">:</span><span class="lit">54</span><span class="pun">-</span><span class="lit">08</span><span class="pun">:</span><span class="lit">00</span></code></li><li class="L1"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">time </span><span class="pun">|</span><span class="pln"> date_to_rfc822 </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="typ">Mon</span><span class="pun">,</span><span class="pln"> </span><span class="lit">07</span><span class="pln"> </span><span class="typ">Nov</span><span class="pln"> </span><span class="lit">2008</span><span class="pln"> </span><span class="lit">13</span><span class="pun">:</span><span class="lit">07</span><span class="pun">:</span><span class="lit">54</span><span class="pln"> </span><span class="pun">-</span><span class="lit">0800</span></code></li><li class="L2"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">time </span><span class="pun">|</span><span class="pln"> date_to_string </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="lit">07</span><span class="pln"> </span><span class="typ">Nov</span><span class="pln"> </span><span class="lit">2008</span></code></li><li class="L3"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">time </span><span class="pun">|</span><span class="pln"> date_to_long_string </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="lit">07</span><span class="pln"> </span><span class="typ">November</span><span class="pln"> </span><span class="lit">2008</span></code></li></ol></pre></div></div>

<h3 id="menuIndex28">搜索指定key</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="com"># Select all the objects in an array where the key has the given value.</span></code></li><li class="L1"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">members </span><span class="pun">|</span><span class="pln"> </span><span class="kwd">where</span><span class="pun">:</span><span class="str">"graduation_year"</span><span class="pun">,</span><span class="str">"2014"</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span></code></li></ol></pre></div></div>

<h3 id="menuIndex29">排序</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">pages </span><span class="pun">|</span><span class="pln"> sort</span><span class="pun">:</span><span class="pln"> </span><span class="str">'title'</span><span class="pun">,</span><span class="pln"> </span><span class="str">'last'</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex30">to json</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">data</span><span class="pun">.</span><span class="pln">projects </span><span class="pun">|</span><span class="pln"> jsonify </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex31">序列化</h3>

<p>把一个对象变成一个字符串</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> page</span><span class="pun">.</span><span class="pln">tags </span><span class="pun">|</span><span class="pln"> array_to_sentence_string </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex32">单词的个数</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> page</span><span class="pun">.</span><span class="pln">content </span><span class="pun">|</span><span class="pln"> number_of_words </span><span class="pun">}</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h3 id="menuIndex33">指定个数</h3>

<p>得到数组指定范围的结果集</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="pun">{</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> </span><span class="kwd">for</span><span class="pln"> post </span><span class="kwd">in</span><span class="pln"> site</span><span class="pun">.</span><span class="pln">posts limit</span><span class="pun">:</span><span class="lit">20</span><span class="pln"> </span><span class="pun">%</span><span class="pln"> </span><span class="pun">}</span></code></li></ol></pre></div></div>

<h2 id="menuIndex34">内容名字规范</h2>

<p>对于博客,名字必须是 YEAR-MONTH-DAY-title.MARKUP 的格式.</p>

<p>比如</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight prettyprint linenums"><ol class="linenums"><li class="L0"><code><span class="lit">2014</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">06</span><span class="pun">-</span><span class="pln">memcached</span><span class="pun">-</span><span class="pln">code</span><span class="pun">.</span><span class="pln">md</span></code></li><li class="L1"><code><span class="lit">2014</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">06</span><span class="pun">-</span><span class="pln">memcached</span><span class="pun">-</span><span class="pln">lib</span><span class="pun">.</span><span class="pln">md</span></code></li><li class="L2"><code><span class="lit">2014</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">06</span><span class="pun">-</span><span class="pln">sphinx</span><span class="pun">-</span><span class="pln">config</span><span class="pun">-</span><span class="kwd">and</span><span class="pun">-</span><span class="kwd">use</span><span class="pun">.</span><span class="pln">md</span></code></li><li class="L3"><code><span class="lit">2014</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">07</span><span class="pun">-</span><span class="pln">memcached</span><span class="pun">-</span><span class="pln">hash</span><span class="pun">-</span><span class="pln">table</span><span class="pun">.</span><span class="pln">md</span></code></li><li class="L4"><code><span class="lit">2014</span><span class="pun">-</span><span class="lit">11</span><span class="pun">-</span><span class="lit">07</span><span class="pun">-</span><span class="pln">memcached</span><span class="pun">-</span><span class="kwd">string</span><span class="pun">-</span><span class="pln">hash</span><span class="pun">.</span><span class="pln">md</span></code></li></ol></pre></div></div>

