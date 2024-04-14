<!-- eslint-disable vue/multiline-html-element-content-newline -->
<!-- eslint-disable vue/first-attribute-linebreak -->
<!-- eslint-disable vue/html-closing-bracket-newline -->
<!-- eslint-disable vue/max-attributes-per-line -->
<!-- eslint-disable vue/html-indent -->
<!-- eslint-disable vue/no-multiple-template-root -->
<!-- eslint-disable vue/no-bare-strings-in-template -->
<!-- eslint-disable vue/no-v-for-template-key -->
<template>


  <div class="dev-portal-products">
    <div class="products-top-section flex flex-col items-center justify-center py-16 bg-section_colors-hero">

      <h1 class="products-title mb-5 font-normal color-text_colors-hero text-4xl">
        {{ product.name }}
      </h1>
      <h5 class="products-title mb-5 font-normal color-text_colors-hero text-4xl">
        Produit par : Team GED
      </h5>
    </div>
  </div>

  <main class="pl-5 md:pl-0 d-flex flex-row" data-testid="api-documentation-page">

    <div class="col content mt-6">

      <div v-if="product && !product.document_count" data-testid="documentation-empty-state">


        <EmptyState>
          <template #title>
            {{ helpText.apiDocumentation.emptyTitle }}
          </template>
          <template #message>
            <p>
              {{ helpText.apiDocumentation.emptyMessage }}
            </p>
          </template>
        </EmptyState>
      </div>

      <KSkeleton v-else-if="isDocumentLoading" />
      <template v-else>
        <header class="content-header">
          <KBreadcrumbs :items="breadcrumbs" />
          <h1 class="content-title color-text_colors-headings">
            {{ title }}
          </h1>
        </header>

        <ErrorWrapper v-if="errorCode" :error-code="errorCode"
          :description="helpText.apiDocumentation.error.description"
          :link-text="helpText.apiDocumentation.error.linkText" />
        <DocumentViewer v-else-if="content" data-testid="portal-document-viewer" class="portal-document-viewer"
          :document="content" />
      </template>
    </div>
    <aside class="col sidebar sidebar-sections">
      <div id="" class="jsx-3352172386 sub-section" style="margin-top:50%">
        <h2 class="jsx-3352172386">Accéder aux données</h2>
        <div>L’API est ouverte à tous. Vous pouvez y accéder dès maintenant :</div> <br>
        <div class="layout-right vertical-margin" >
        <router-link
        :to="`/docs/${product.id}/Documentation`"
      ><a class="fcc-btn"><span role="img" aria-label="emoji code"
                class="jsx-9c4286d73ae80ec8">👩&zwj;💻</span>Tester l’API</a></router-link></div>
        <br>
      </div>
      <KSkeleton v-if="product?.document_count && isDocumentLoading" class="skeleton" />
      <DocumentSections v-else :items="sections" />
    </aside>
  </main>

  <!-- <main data-v-189367c5="" data-v-a97bb8eb="" class="pl-5 md:pl-0 d-flex flex-row" data-testid="api-documentation-page">
    <div data-v-189367c5="" class="col content mt-6">
      <header data-v-189367c5="" class="content-header">
        <ul data-v-949c19bf="" data-v-189367c5="" class="k-breadcrumbs">
          <li data-v-949c19bf="" class="k-breadcrumbs-item"><a data-v-949c19bf="" href="/"
              class="router-link-active no-underline">
              <div data-v-949c19bf="" class="k-breadcrumb-icon-wrapper"></div><span data-v-949c19bf=""
                class="k-breadcrumb-text" style="max-width: 38ch;">Catalog</span>
            </a><span data-v-949c19bf="" class="k-breadcrumb-divider"><span data-v-32539fc3="" data-v-949c19bf=""
                class="kong-icon kong-icon-chevronRight"><svg viewBox="0 0 20 20"
                  fill="var(--grey-500, var(--kui-color-text-neutral-weak, #afb7c5))" xmlns="http://www.w3.org/2000/svg"
                  role="img" width="16px" height="16px">

                  <path d="m7.3 14.7 5-5.2-5-5.2" fill="none"
                    stroke="var(--grey-500, var(--kui-color-text-neutral-weak, #afb7c5))" stroke-width="2"
                    stroke-linecap="round" stroke-linejoin="round"></path>
                </svg>
              </span></span></li>

          <li data-v-949c19bf="" class="k-breadcrumbs-item"><a data-v-949c19bf=""
              href="/docs/d6e66771-76ab-4193-9ba3-b14f933a2e5f" class="router-link-active no-underline">
              <div data-v-949c19bf="" class="k-breadcrumb-icon-wrapper"></div><span data-v-949c19bf=""
                class="k-breadcrumb-text" style="max-width: 38ch;">Présentation</span>
            </a><span data-v-949c19bf="" class="k-breadcrumb-divider"><span data-v-32539fc3="" data-v-949c19bf=""
                class="kong-icon kong-icon-chevronRight"><svg viewBox="0 0 20 20"
                  fill="var(--grey-500, var(--kui-color-text-neutral-weak, #afb7c5))" xmlns="http://www.w3.org/2000/svg"
                  role="img" width="16px" height="16px">

                  <path d="m7.3 14.7 5-5.2-5-5.2" fill="none"
                    stroke="var(--grey-500, var(--kui-color-text-neutral-weak, #afb7c5))" stroke-width="2"
                    stroke-linecap="round" stroke-linejoin="round"></path>
                </svg>
              </span></span></li>
        </ul>
        <h1 data-v-189367c5="" class="content-title color-text_colors-headings">Présentation</h1>
      </header>
      <div data-v-1ab71c85="" data-v-189367c5="" class="document-viewer portal-document-viewer"
        data-testid="portal-document-viewer">
        <hr data-v-b6e25b56="">
        <h2 data-v-9ef4ad64="" id="doc-heading-cest-quoi-lapi-ged-de-covea-">C'est quoi l'API GED de Covea
          ?</h2>
        <p data-v-7b54f530="">L'une des raisons majeures du déploiement de la GED Covea est de limiter l’absence de
          collaboration entre le logiciel de Gestion Électronique des Documents et les autres systèmes déjà en place, ou
          à venir, dans l’écosystème informatique de l’organisation. Les API permettent l’interopérabilité de ces
          systèmes hétérogènes et, à un degré plus fin encore, l’interopérabilité de leurs données.</p>
        <p data-v-7b54f530="">Le fonctionnement des API repose sur un accord d’entrées et de sorties : le logiciel
          source reçoit une requête (query) émanant d’un système tiers, qu’il interprète et valide, sous réserve
          d’autorisation, en donnant accès aux contenus demandés</p>
        <p data-v-7b54f530="">Développer et déployer des API rend possible l’interopérabilité de la GED d’une
          organisation en permettant aux systèmes et programmes utilisés dans les différents services et métiers de
          collaborer avec le logiciel de Gestion Électronique des Documents indépendamment de la compatibilité de leur
          langage de programmation respectif.</p>
        <h2 data-v-9ef4ad64="" id="doc-heading-comment-effectuer-une-demande-de-consommation-dapi--">Comment effectuer
          une demande de consommation d'API ?</h2>
        <blockquote data-v-afdbfde6="">
          <table data-v-c2502730="" alignments="none,none,none" parent="[object Object]">
            <tbody data-v-90ab3ded="" alignments="" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <th data-v-6fde1a24="" class="">Etape</th>
                <th data-v-6fde1a24="" class="">Description</th>
                <th data-v-6fde1a24="" class="">Acteurs</th>
              </tr>
            </tbody>
            <tbody data-v-90ab3ded="" alignments="none,none,none" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <td data-v-6fde1a24="" class=""><code data-v-cbde41ab="" parent="[object Object]">1</code>
                </td>
                <td data-v-6fde1a24="" class="">Création de la demande de consommation via le portail API
                </td>
                <td data-v-6fde1a24="" class="">Consomateurs</td>
              </tr>
            </tbody>
            <tbody data-v-90ab3ded="" alignments="none,none,none" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <td data-v-6fde1a24="" class=""><code data-v-cbde41ab="" parent="[object Object]">2</code>
                </td>
                <td data-v-6fde1a24="" class="">Validation de la demande de consommation</td>
                <td data-v-6fde1a24="" class="">API Product Owner Platform</td>
              </tr>
            </tbody>
            <tbody data-v-90ab3ded="" alignments="none,none,none" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <td data-v-6fde1a24="" class=""><code data-v-cbde41ab="" parent="[object Object]">3</code>
                </td>
                <td data-v-6fde1a24="" class="">Saisie des informations complementaires via une fiche d'inscription (Nom
                  du consommateur, positionnement, Volumetrie, etc.)</td>
                <td data-v-6fde1a24="" class="">Consomateurs</td>
              </tr>
            </tbody>
            <tbody data-v-90ab3ded="" alignments="none,none,none" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <td data-v-6fde1a24="" class=""><code data-v-cbde41ab="" parent="[object Object]">4</code>
                </td>
                <td data-v-6fde1a24="" class="">Validation de la fiche d'inscription API</td>
                <td data-v-6fde1a24="" class="">API Product Owner Platform</td>
              </tr>
            </tbody>
            <tbody data-v-90ab3ded="" alignments="none,none,none" parent="[object Object]">
              <tr data-v-90ab3ded="">
                <td data-v-6fde1a24="" class=""><code data-v-cbde41ab="" parent="[object Object]">5</code>
                </td>
                <td data-v-6fde1a24="" class="">Création des comptes APIM (par environnement) et communication des
                  informations de consommation (URL, credentials, collection Postman et swagger) au consommateur Cette
                  étape permet au consommateur d'appeler l'API au travers de l'APIM. Néanmoins pour que le service
                  offert soit pleinement opérationnel, il se peut que des étapes de configuration technique soient
                  nécessaires. Dans ce cas, une date prévisionnelle cible de bonne marche pourra être
                  transmise.</td>
                <td data-v-6fde1a24="" class="">API Product Owner Platform</td>
              </tr>
            </tbody>
          </table>
        </blockquote>
        <h2 data-v-9ef4ad64="" id="doc-heading-comment-tester-une-api-">Comment tester une API ?</h2>
        <p data-v-7b54f530="">Afin d'effectuer des premiers tests à votre API au travers de l'APIM, la mécanique d'appel
          s'éffectue en deux temps :</p>
        <ul data-v-7555911f="" class="">
          <li data-v-cf238e78="" parent="[object Object]">
            <p data-v-7b54f530="" parent="[object Object]">Étape 1 : Récupération du token APIM à l'aide des credentials
              transmis (ClientId et ClienSecret)</p>
          </li>
          <li data-v-cf238e78="" parent="[object Object]">
            <p data-v-7b54f530="" parent="[object Object]">Étape 2 : Appel à l'API en passant en bearer le token APIM
              récupéré lors de l'étape 1.</p>
          </li>
        </ul>
        <h2 data-v-9ef4ad64="" id="doc-heading-comment-intgrer-lapi-dans-mon-application-">Comment intégrer l'API dans
          mon application ?</h2>
        <p data-v-7b54f530="">Les API GED de Covea sont toutes basées sur une architecture REST, leur contrat
          d'interface est défini via la norme OpenAPI 3.0 (Swagger) et les données transmises au format JSON en
          respectant les normes ISO pour les dates notamment.</p>
        <p data-v-7b54f530="">Vous pouvez importer ce contrat comme vous le souhaitez, en utilisant votre technologie
          préférée ; étant basé sur HTTP, l'architecture REST ne demande pas de connecteur ou librairie
          particulière.</p>
        <p data-v-7b54f530="">Il est cependant plus pratique de générer les objets (DTO) qui reflètent nos objets
          métiers pour pouvoir les manipuler : attention à ne garder que les attributs qui vous intéressent et à
          indiquer à votre implémentation d'ignorer les attributs supplémentaires.</p>
        <p data-v-7b54f530="">Dans un premier temps il est nécessaire de s'identifier en suivant les modalités décrites
          dans l’annexe Gestion de l'authentification.</p>
        <p data-v-7b54f530="">Vous pouvez ensuite utiliser le token d'authentification dans les appels
          successifs.</p>
        <h2 data-v-9ef4ad64="" id="doc-heading-quels-sont-les-cots-induits-">Quels sont les coûts induits
          ?</h2>
        <p data-v-7b54f530="">Les coûts sont définis dans les conditions contractuelles du partenariat.
        </p>
        <h2 data-v-9ef4ad64="" id="doc-heading-comment-suivre-lutilisation-de-mon-api-">Comment suivre l'utilisation de
          mon API ?</h2>
        <p data-v-7b54f530="">Dans l'immédiat, les statistiques d'utilisation ne sont pas disponibles et seront
          intégrées au portail API avant la fin de l’année.</p>
        <h2 data-v-9ef4ad64="" id="doc-heading-qui-contacter-en-cas-de-problme-ou-comment-faire-des-feedbacks-">Qui
          contacter en cas de problème ou Comment faire des feedbacks ?</h2>
        <p data-v-7b54f530="">En cas de problème relatif à l'utilisation des API métiers, j'utilise le formulaire de
          contact du portail API : un ticket sera créé et je serai recontacté sous les délais définis
          contractuellement.</p>
      </div>
    </div>
    <aside data-v-189367c5="" class="col sidebar sidebar-sections" style="margin-top:10%">
      <div data-v-6a855f02="" data-v-189367c5="" class="wrapper">
        <div class="jsx-2644042042 right-column info-column">
          <div id="" class="jsx-3352172386 sub-section">
            <h2 class="jsx-3352172386">Accéder aux données</h2>
            <div>L’API est ouverte à tous. Vous pouvez y accéder dès maintenant :</div> <br>
            <div class="layout-right vertical-margin"><a rel="" target="" class="fr-btn  "
                href="/documentation/api-geo">
                <div class="content-wrapper"><a href=""  class="fcc-btn"><span role="img" aria-label="emoji code"
                    class="jsx-9c4286d73ae80ec8">👩&zwj;💻</span>Tester l’API</a></div>
              </a></div> <br>
          </div>
          <div id="" class="jsx-3352172386 sub-section">
            <h2 class="jsx-3352172386">L’équipe</h2>
            <div class="jsx-bd9c59f631294483">Cette API est produite par :</div>
            <div class="jsx-bd9c59f631294483 team"><img src="/images/api-logo/dinum.png" alt=""
                class="jsx-bd9c59f631294483"><span class="jsx-bd9c59f631294483"><a href="/producteurs/dinum"
                  class="jsx-bd9c59f631294483">Direction Interministérielle du Numérique (DINUM)</a></span>
            </div>
            <div class="jsx-bd9c59f631294483 layout-right vertical-margin"><a class="fr-btn fr-btn--secondary "
                href="mailto:alfred.ado.ext@groupe-mma.fr?subject=Contact%20via%20mma.fr">
                <div class="content-wrapper"><span role="img" aria-label="émoji mail"
                    class="jsx-bd9c59f631294483">💌</span> Écrire un mail à l’équipe</div>
              </a></div>
          </div>
        </div>
      </div>
    </aside>
  </main> -->
</template>

<script lang="ts">
import { defineComponent, computed, ref, watchEffect, PropType } from 'vue'
import { useRouter } from 'vue-router'
import { storeToRefs } from 'pinia'
import getMessageFromError from '@/helpers/getMessageFromError'
import usePortalApi from '@/hooks/usePortalApi'
import DocumentSections from '@/components/ApiDocumentation/DocumentSections.vue'
import ErrorWrapper from '@/components/ErrorWrapper.vue'
import { findAllNodesOfType, getNodeTextContent } from '@/helpers/document'
import { ProductWithVersions, useI18nStore, useProductStore } from '@/stores'
import useToaster from '@/composables/useToaster'
import DocumentViewer, { HeadingNode, addSlug } from '@kong-ui-public/document-viewer'

import '@kong-ui-public/document-viewer/dist/style.css'
import { DocumentBlock, ProductDocument } from '@kong/sdk-portal-js'

export default defineComponent({
  name: 'PresentationPage',
  components: {
    DocumentViewer,
    DocumentSections,
    ErrorWrapper
  },
  props: {
    product: {
      type: Object as PropType<ProductWithVersions>,
      required: true
    }
  },
  setup(props) {
    const helpText = useI18nStore().state.helpText
    const productStore = useProductStore()
    const { activeDocumentSlug } = storeToRefs(productStore)

    const { notify } = useToaster()
    const errorCode = ref(null)
    const router = useRouter()
    const { portalApiV2 } = usePortalApi()

    const breadcrumbs = computed(() => ([
      {
        key: 'product-catalog',
        to: { name: 'catalog' },
        text: helpText.nav.catalog
      },
      {
        key: 'product',
        to: props.product
          ? {
            name: 'spec',
            params: {
              product: props.product.id
            }
          }
          : undefined,
        text: props.product?.name || (helpText.nav.breadcrumbProduct)
      },
      {
        key: 'presentation',
        text: helpText.nav.breadcrumbDocumentation,
        to: props.product
          ? {
            name: 'presentation-page',
            params: {
              product: props.product.id
            }
          }
          : undefined
      }
    ]))

    const title = ref<string>(null)
    const isDocumentLoading = ref<boolean>(true)
    const content = ref<DocumentBlock>(null)

    const sections = computed(() => {
      if (!content.value) {
        return []
      }

      // this is to prevent duplicate slugs
      const slugMap = new Map<string, number>()

      const allHeadings = findAllNodesOfType<DocumentBlock>(content.value, 'heading') as unknown as HeadingNode[]

      return allHeadings
        .map((node) => {
          const text = getNodeTextContent(node)
          const { slug } = addSlug(node, slugMap)
          const level = getMaxHeaderLevel(2)

          return {
            level,
            slug,
            title: text
          }

          function getMaxHeaderLevel(maxHeadingLevel) {
            return Math.min(node.level, maxHeadingLevel)
          }
        })
    })

    async function fetchDocument(productId: string, slug: string) {
      errorCode.value = null
      isDocumentLoading.value = true

      await portalApiV2.value.service.documentationApi.getProductDocument({
        productId,
        documentId: slug
      }, {
        headers: {
          accept: 'application/vnd.konnect.document-nodes+json'
        }
      })
        .then((res) => {
          const data = res.data as unknown as ProductDocument // override

          title.value = data.title
          content.value = data.content
          productStore.setActiveDocumentId(data.id)
        })
        .finally(() => {
          isDocumentLoading.value = false
        })
    }

    const handleError = (error) => {
      notify({
        appearance: 'danger',
        message: getMessageFromError(error)
      })

      const statusCode = error?.response?.status || 400

      if (statusCode !== 404) {
        errorCode.value = statusCode
      } else {
        router.replace({
          name: 'not-found'
        })
      }
    }

    watchEffect(async () => {
      if (activeDocumentSlug.value && props.product) {
        try {
          await fetchDocument(props.product.id, activeDocumentSlug.value)
        } catch (e) {
          handleError(e)
        }
      }
    })

    return {
      helpText,
      title,
      content,
      isDocumentLoading,
      sections,
      breadcrumbs,
      document,
      errorCode,
      slug: activeDocumentSlug.value
    }
  }
})
</script>

<style lang="scss">
.portal-document-viewer {
  pre {
    overflow-x: auto;
  }
}
</style>

<style lang="scss" scoped>
.skeleton {
  margin-top: 2rem;
}

/* Create two unequal columns that floats next to each other */
.column {
  float: left;
  height: 100vh;
  /* Should be removed. Only for demonstration */
}

.left {
  width: 65%;
}

.right {
  width: 35%;
}

.fcc-btn {
  background-color: #223094;
  color: white;
  padding: 15px 25px;
  text-decoration: none;
  margin: auto;
}

.fcc-btn:hover {
  background-color: #223094;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

.col {
  flex: 0 0 auto;
  padding: 0 0.75rem;

  &:first-child {
    padding-left: 0;
  }

  &:last-child {
    padding-right: 0;
  }
}

.sidebar {
  flex-basis: 25%;
}

.content {
  flex: 1 1 60%;
  overflow-x: auto;
}

.content-title {
  font-size: 2rem;
}

.content-header {
  margin-bottom: var(--spacing-xxl);
}

.sidebar-sections {
  display: none;

  @media (min-width: 992px) {
    display: block;
  }
}

.documents {
  margin-top: 2rem;
}

.documents-title {
  display: block;
  font-size: 1.25rem;
  margin: 0 0 0.75rem;
  color: var(--text_colors-headings);
  font-family: var(--font-family-headings);
}

.portal-document-viewer {
  --kong-ui-document-viewer-font-family-default: var(--font-family-sans);
  --kong-ui-document-viewer-font-family-monospace: var(--font-family-mono);
  --kong-ui-document-viewer-font-family-headings: var(--font-family-headings);
  --kong-ui-document-viewer-link-color: var(--text_colors-link);
  --kong-ui-document-viewer-link-hover-color: var(--text_colors-accent);
  --kong-ui-document-viewer-color: var(--text_colors-primary);
  --kong-ui-document-viewer-code-color: var(--steel-700, #0a2b66);

  // This is going to solve some contrast issues with blockquotes
  // and their text colors.

  --kong-ui-document-viewer-code-color: var(--steel-700, #0a2b66);

  :deep(blockquote) {
    color: var(--steel-700, #0a2b66);

    h1,
    h2,
    h3,
    h4,
    h5,
    h6 {
      color: var(--steel-700, #0a2b66);
    }
  }
}
</style>
