---
layout: page
title: Capacitações
permalink: /capacitacoes/
---

Esta seção reúne as capacitações oferecidas pela PotiCode aos seus membros.

{% for semana in site.data.capacitacoes.semanas %}
<h3 class="training-week-label">{{ semana.label }}</h3>
<ul class="training-list">
  {% for sessao in semana.sessoes %}
  <li data-unlock="{{ sessao.unlock }}">
    <a href="{{ '/capacitacoes/' | append: sessao.slug | append: '/' | relative_url }}">{{ sessao.titulo }}</a>
  </li>
  {% endfor %}
</ul>
{% endfor %}

<script>
(function () {
  var today = new Date();
  today.setHours(0, 0, 0, 0);
  document.querySelectorAll('.training-list li[data-unlock]').forEach(function (li) {
    var unlock = new Date(li.dataset.unlock);
    if (unlock > today) {
      li.classList.add('locked');
      var a = li.querySelector('a');
      if (a) {
        a.removeAttribute('href');
        a.setAttribute('aria-disabled', 'true');
      }
    }
  });
})();
</script>
