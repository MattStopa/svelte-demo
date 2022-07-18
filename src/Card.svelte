<script>
  export let title = 'asdf'
</script>

<div class="px-3 py-4 overflow-y-auto rounded bg-gray-50 dark:bg-gray-800">
  <div class="text-2xl font-bold text-gray-800 text-left mb-5">{title}</div>
  <slot></slot>
</div>