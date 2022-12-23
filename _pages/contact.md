---
title: Contact Me
layout: page
permalink: /contact/
---

<!-- modify this form HTML and place wherever you want your form -->

<form
  action="{{site.data.settings.formspree-action}}"
  method="POST"
>
	<div class="grid gap-4">

  <label>
    Your email:  </label>
    <input class="border py-2 px-3 text-grey-darkest rounded" type="email" name="_replyto">

  <label>
    Your message:  </label>
    <textarea class="border py-2 px-3 text-grey-darkest rounded" name="message" rows="6"></textarea>

  <!-- your other form fields go here -->

<button class="grid bg-green-500 border-b-4 border-green-600 rounded px-4 py-3 text-center text-white font-bold hover:bg-green-400 hover:border-opacity-0 transform duration-300" type="submit">Send</button>

</div>

</form>
