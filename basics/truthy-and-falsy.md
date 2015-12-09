---
title: Truthy and falsy
---

In programming, anything that returns `true` in a conditional is called **truthy**. Anything that returns `false` in a conditional is called **falsy**. All object types can be described as either truthy or falsy.

## Truthy

All values in Liquid are truthy except `nil` and `false`.

In the example below, the text "Tobi" is not a boolean, but it is truthy in a conditional:

{% highlight liquid %}{% raw %}
{% assign tobi = 'Tobi' %}

{% if tobi == true %}
  This condition will always be true.
{% endif %}
{% endraw %}{% endhighlight %}

[Strings](/basics/types/#string), even when empty, are truthy. The example below will result in empty HTML tags if `settings.fp_heading` is empty:

<div class="code-block code-block--input">
{% highlight html %}{% raw %}
{% if settings.fp_heading %}
  <h1>{{ settings.fp_heading }}</h1>
{% endif %}
{% endraw %}{% endhighlight %}
</div>

<div class="code-block code-block--output">
{% highlight html %}{% raw %}
<h1></h1>
{% endraw %}{% endhighlight %}
</div>

[EmptyDrops](/basics/types/#emptydrop) are also truthy. In the example below, if `settings.page` is an empty string or set to a hidden or deleted object, you will end up with an EmptyDrop. The result is an empty div:

<div class="code-block code-block--input">
{% highlight html %}{% raw %}
{% if pages[settings.page] %}
  <div>{{ pages[settings.page].content }}</div>
{% endif %}
{% endraw %}{% endhighlight %}
</div>

<div class="code-block code-block--output">
{% highlight html %}{% raw %}
<div></div>
{% endraw %}{% endhighlight %}
</div>

## Falsy

The falsy values in Liquid are [nil](/basics/types/#nil) and [false](/basics/types/#boolean).

## Summary

The table below summarizes what is truthy or falsy in Liquid.

|               | truthy        | falsy         |
| ------------- |:-------------:|:-------------:|
| true          | •             |               |
| false         |               | •             |
| nil           |               | •             |
| string        | •             |               |
| empty string  | •             |               |
| 0             | •             |               |
| integer       | •             |               |
| float         | •             |               |
| array         | •             |               |
| empty array   | •             |               |
| page          | •             |               |
| EmptyDrop     | •             |               |