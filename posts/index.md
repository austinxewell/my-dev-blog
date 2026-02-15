---
layout: page
title: Posts
permalink: /posts/
nav: true
---

<input
  type="text"
  id="post-search"
  placeholder="Search posts by title or tag..."
  class="post-search"
/>

{% include post-list.html
   heading=""
   exclude_category="personal-blog"
%}

<script>
const searchInput = document.getElementById('post-search');

if (searchInput) {
  searchInput.addEventListener('input', e => {
    const query = e.target.value.toLowerCase();

    document.querySelectorAll('.post-list li').forEach(li => {
      const title = li.dataset.title || "";
      const tags = li.dataset.tags || "";

      li.style.display =
        title.includes(query) ||
        tags.includes(query)
          ? ''
          : 'none';
    });
  });
}
</script>
