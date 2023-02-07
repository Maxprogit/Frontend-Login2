 <template>
    <div style="padding: 20px;">
        <Principal />
    </div>
 </template>

 <script>
import Principal from '~/components/dashboard/principal.vue';

    export default{
        auth: true,
        layout: 'dashboard',
        components: {
            Principal
        }
    }
</script>