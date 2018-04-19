<template>
    <div class="mt-3">
        <h3>My Quotes</h3>
        <div class="progress">
            <div class="progress-bar progress-bar-striped" 
                role="progressbar" 
                :style="{width: (quoteCount / maxQuotes) * 100 + '%'}" 
                aria-valuenow="10" 
                aria-valuemin="0" 
                aria-valuemax="100"
            >
                {{ quoteCount }} / {{ maxQuotes }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["quoteCount", "maxQuotes"]
};
</script>