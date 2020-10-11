<template>
<div class="mw6 center pa3 sans-serif">
            <h1 class="mb4">Contacts</h1>

            <div class="pa2 mb3 striped--near-white">
                <header class="b mb2">{{ contact.name }}</header>
                <div class="pl2">
                    <p class="mb2">{{ contact.phone }}</p>
                    <p class="pre mb3">{{ contact.address }}</p>
                    <p class="mb2">{{ contact.email }}</p>
                </div>
            </div>
        </div>
</template>
<script>
export default {
    props: ["contact"]
};
</script>
   