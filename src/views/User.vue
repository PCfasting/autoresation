<template>
    <div>
        Привет, {{user.name}}
    </div>
</template>

<script>
export default {
    props: {
        'user'
    }   
}
</script>