<!--
  Matomo - free/libre analytics platform
  @link https://matomo.org
  @license http://www.gnu.org/licenses/gpl-3.0.html GPL v3 or later
-->

<template>
  <ContentBlock
    :content-title="translate('UsersManager_TokenSuccessfullyGenerated')"
  >
    <p>
      {{ translate('UsersManager_PleaseStoreToken') }}
      <br>
      {{ translate('UsersManager_DoNotStoreToken') }}
    </p>
    <pre v-select-on-focus="{}"
         style="font-size: 40px;"
         class="generatedTokenAuth"
    ><code>{{ generatedToken }}</code></pre>

    <a :href="userSecurityLink" class="btn" style="height:auto">
      {{ translate('UsersManager_ConfirmTokenCopied') }}
      {{ translate('UsersManager_GoBackSecurityPage') }}
    </a>
  </ContentBlock>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { ContentBlock, SelectOnFocus, MatomoUrl } from 'CoreHome';

export default defineComponent({
  props: {
    generatedToken: {
      type: String,
      required: true,
    },
  },
  components: {
    ContentBlock,
  },
  directives: {
    SelectOnFocus,
  },
  computed: {
    userSecurityLink() {
      return `?${MatomoUrl.stringify({
        ...MatomoUrl.urlParsed.value,
        module: 'UsersManager',
        action: 'userSecurity',
      })}`;
    },
  },
});
</script>
