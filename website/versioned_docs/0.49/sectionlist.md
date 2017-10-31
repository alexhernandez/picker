---
id: version-0.49-sectionlist
title: sectionlist
original_id: sectionlist
---
<a id="content"></a><h1><a class="anchor" name="sectionlist"></a>SectionList <a class="hash-link" href="docs/sectionlist.html#sectionlist">#</a></h1><div><div><p>A performant interface for rendering sectioned lists, supporting the most handy features:</p><ul><li>Fully cross-platform.</li><li>Configurable viewability callbacks.</li><li>List header support.</li><li>List footer support.</li><li>Item separator support.</li><li>Section header support.</li><li>Section separator support.</li><li>Heterogeneous data and item rendering support.</li><li>Pull to Refresh.</li><li>Scroll loading.</li></ul><p>If you don't need section support and want a simpler interface, use
<a href="/react-native/docs/flatlist.html" target=""><code>&lt;FlatList&gt;</code></a>.</p><p>Simple Examples:</p><div class="prism language-javascript"><span class="token operator">&lt;</span>SectionList
  renderItem<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">(</span><span class="token punctuation">{</span>item<span class="token punctuation">}</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token operator">&lt;</span>ListItem title<span class="token operator">=</span><span class="token punctuation">{</span>item<span class="token punctuation">}</span> <span class="token operator">/</span><span class="token operator">&gt;</span><span class="token punctuation">}</span>
  renderSectionHeader<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">(</span><span class="token punctuation">{</span>section<span class="token punctuation">}</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token operator">&lt;</span>Header title<span class="token operator">=</span><span class="token punctuation">{</span>section<span class="token punctuation">.</span>title<span class="token punctuation">}</span> <span class="token operator">/</span><span class="token operator">&gt;</span><span class="token punctuation">}</span>
  sections<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">[</span><span class="token comment" spellcheck="true"> // homogenous rendering between sections
</span>    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> title<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> title<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> title<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">]</span><span class="token punctuation">}</span>
<span class="token operator">/</span><span class="token operator">&gt;</span>

<span class="token operator">&lt;</span>SectionList
  sections<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">[</span><span class="token comment" spellcheck="true"> // heterogeneous rendering between sections
</span>    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> renderItem<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> renderItem<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>data<span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token operator">...</span><span class="token punctuation">]</span><span class="token punctuation">,</span> renderItem<span class="token punctuation">:</span> <span class="token operator">...</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">]</span><span class="token punctuation">}</span>
<span class="token operator">/</span><span class="token operator">&gt;</span></div><p>This is a convenience wrapper around <a href="docs/virtualizedlist.html" target="_blank"><code>&lt;VirtualizedList&gt;</code></a>,
and thus inherits its props (as well as those of <code>ScrollView</code>) that aren't explicitly listed
here, along with the following caveats:</p><ul><li>Internal state is not preserved when content scrolls out of the render window. Make sure all
your data is captured in the item data or external stores like Flux, Redux, or Relay.</li><li>This is a <code>PureComponent</code> which means that it will not re-render if <code>props</code> remain shallow-
equal. Make sure that everything your <code>renderItem</code> function depends on is passed as a prop
(e.g. <code>extraData</code>) that is not <code>===</code> after updates, otherwise your UI may not update on
changes. This includes the <code>data</code> prop and parent component state.</li><li>In order to constrain memory and enable smooth scrolling, content is rendered asynchronously
offscreen. This means it's possible to scroll faster than the fill rate and momentarily see
blank content. This is a tradeoff that can be adjusted to suit the needs of each application,
and we are working on improving it behind the scenes.</li><li>By default, the list looks for a <code>key</code> prop on each item and uses that for the React key.
Alternatively, you can provide a custom <code>keyExtractor</code> prop.</li></ul></div><h3><a class="anchor" name="props"></a>Props <a class="hash-link" href="docs/sectionlist.html#props">#</a></h3><div class="props"><div class="prop"><h4 class="propTitle"><a class="anchor" name="stickysectionheadersenabled"></a>stickySectionHeadersEnabled?:  <a class="hash-link" href="docs/sectionlist.html#stickysectionheadersenabled">#</a></h4></div></div><span><h3><a class="anchor" name="methods"></a>Methods <a class="hash-link" href="docs/sectionlist.html#methods">#</a></h3><div class="props"><div class="prop"><h4 class="methodTitle"><a class="anchor" name="scrolltolocation"></a>scrollToLocation<span class="methodType">(params: object)</span> <a class="hash-link" href="docs/sectionlist.html#scrolltolocation">#</a></h4><div><p>Scrolls to the item at the specified <code>sectionIndex</code> and <code>itemIndex</code> (within the section)
positioned in the viewable area such that <code>viewPosition</code> 0 places it at the top (and may be
covered by a sticky header), 1 at the bottom, and 0.5 centered in the middle. <code>viewOffset</code> is a
fixed number of pixels to offset the final target position, e.g. to compensate for sticky
headers.</p><p>Note: cannot scroll to locations outside the render window without specifying the
<code>getItemLayout</code> prop.</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="recordinteraction"></a>recordInteraction<span class="methodType">()</span> <a class="hash-link" href="docs/sectionlist.html#recordinteraction">#</a></h4><div><p>Tells the list an interaction has occured, which should trigger viewability calculations, e.g.
if <code>waitForInteractions</code> is true and the user has not scrolled. This is typically called by
taps on items or by navigation actions.</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="flashscrollindicators"></a>flashScrollIndicators<span class="methodType">()</span> <a class="hash-link" href="docs/sectionlist.html#flashscrollindicators">#</a></h4><div><p>Displays the scroll indicators momentarily.</p></div></div></div></span></div><p class="edit-page-block"><a target="_blank" href="https://github.com/facebook/react-native/blob/master/Libraries/Lists/SectionList.js">Improve this page</a> by sending a pull request!</p><div class="docs-prevnext"><a class="docs-prev" href="docs/scrollview.html#content">← Prev</a><a class="docs-next" href="docs/segmentedcontrolios.html#content">Next →</a></div>