<!-- bookstack/resources/views/parts/custom-editor-script.blade.php -->
<script>
window.addEventListener('editor-tinymce::pre-init', event => {
    const mceConfig = event.detail.config;
    
    // Adiciona o plugin 'searchreplace' à lista de plugins do TinyMCE
    if (mceConfig.plugins) {
        mceConfig.plugins += ' searchreplace';
    }
    
    // Adiciona o botão na barra de ferramentas (toolbar)
    if (mceConfig.toolbar) {
        mceConfig.toolbar += ' | searchreplace';
    }
});
</script>