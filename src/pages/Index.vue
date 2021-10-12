<template>
  <q-page>
    <!-- <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
    ></example-component> -->
    <q-parallax src="https://source.unsplash.com/collection/171168/1200x900">
      <div
        style="
          position: absolute;
          background: black;
          width: 100%;
          height: 100%;
          filter: opacity(40%) saturate(30%);
        "
      ></div>
      <div style="z-index: 1">
        <h1 class="text-white">Basic</h1>
        <div class="flex" style="gap: 12px">
          <q-btn color="primary" label="Primary" />
          <q-btn color="secondary" label="Secondary" />
        </div>
      </div>
    </q-parallax>
    <div class="flex q-pa-lg items-center justify-center">
      <q-card class="q-pa-lg q-ma-lg" flat>
        <q-card-section class="text-h4 flex items-center"><q-icon color="primary" name="dashboard" />Default</q-card-section>
        <q-card-section style="max-width: 300px;"
          >Lorem ipsum dolor sit, amet consectetur adipisicing elit. Odio eaque
          consequuntur dolor asperiores id praesentium molestiae inventore velit
          dicta laborum enim cum debitis tempora, est aliquam quibusdam alias
          recusandae ipsam.</q-card-section
        >
      </q-card>
      <q-card class="q-pa-lg q-ma-lg" flat>
        <q-card-section class="text-h4 flex items-center"><q-icon color="primary" name="account_circle" />Default</q-card-section>
        <q-card-section style="max-width: 300px;"
          >Lorem ipsum dolor sit, amet consectetur adipisicing elit. Odio eaque
          consequuntur dolor asperiores id praesentium molestiae inventore velit
          dicta laborum enim cum debitis tempora, est aliquam quibusdam alias
          recusandae ipsam.</q-card-section
        >
      </q-card>
      <q-card class="q-pa-lg q-ma-lg" flat>
        <q-card-section class="text-h4 flex items-center"><q-icon color="primary" name="work" />Default</q-card-section>
        <q-card-section style="max-width: 300px;"
          >Lorem ipsum dolor sit, amet consectetur adipisicing elit. Odio eaque
          consequuntur dolor asperiores id praesentium molestiae inventore velit
          dicta laborum enim cum debitis tempora, est aliquam quibusdam alias
          recusandae ipsam.</q-card-section
        >
      </q-card>
    </div>
    <q-card class="bg-light text-dark" flat square>
      <q-card-section>
        <div class="flex justify-center" style="gap: 12px">
          <div>
            <div class="text-h4 q-pb-md">Primary</div>
            <q-card class="text-center shadow-15" square>
              <q-card-section
                class="bg-primary"
                style="width: 200px; height: 140px"
              ></q-card-section>
            </q-card>
          </div>
          <div>
            <div class="text-h4 q-pb-md">Secondary</div>
            <q-card class="text-center shadow-15" square>
              <q-card-section
                class="bg-secondary"
                style="width: 200px; height: 140px"
              ></q-card-section>
            </q-card>
          </div>
          <div>
            <div class="text-h4 q-pb-md">Accent</div>
            <q-card class="text-center shadow-15" square>
              <q-card-section
                class="bg-accent"
                style="width: 200px; height: 140px"
              ></q-card-section>
            </q-card>
          </div>
          <div>
            <div class="text-h4 q-pb-md">Light</div>
            <q-card class="text-center shadow-15" square>
              <q-card-section
                class="bg-light text-dark"
                style="width: 200px; height: 140px"
              ></q-card-section>
            </q-card>
          </div>
          <div>
            <div class="text-h4 q-pb-md">Dark</div>
            <q-card class="text-center shadow-15" square>
              <q-card-section
                class="bg-dark"
                style="width: 200px; height: 140px"
              ></q-card-section>
            </q-card>
          </div>
        </div>
      </q-card-section>
    </q-card>
    <q-card class="bg-dark">
      <q-card-section class="flex" style="gap: 12px">
        <q-card class="bg-dark text-light" flat>
          <q-card-section class="text-h5">Light on Dark</q-card-section>
          <q-card-section
            >Lorem ipsum, dolor sit amet consectetur adipisicing
            elit.</q-card-section
          >
        </q-card>
        <q-card>
          <q-card-actions align="center">
            <q-chip
              class="glossy"
              square
              color="positive"
              text-color="white"
              icon="check"
            >
              Positive
            </q-chip>
            <q-chip
              class="glossy"
              square
              color="negative"
              text-color="white"
              icon="close"
            >
              Negative
            </q-chip>
            <q-chip
              class="glossy"
              square
              color="info"
              text-color="white"
              icon="info"
            >
              Info
            </q-chip>
            <q-chip
              class="glossy"
              square
              color="warning"
              text-color="white"
              icon="warning"
            >
              Warning
            </q-chip>
          </q-card-actions>
        </q-card>
        <q-card class="bg-accent text-light">
          <q-card-section class="text-h5">Accents</q-card-section>
          <q-card-section
            >Lorem ipsum, dolor sit amet consectetur adipisicing
            elit.</q-card-section
          >
        </q-card>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models';
// import ExampleComponent from 'components/CompositionComponent.vue';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  // components: { ExampleComponent },
  setup() {
    const todos = ref<Todo[]>([
      {
        id: 1,
        content: 'ct1',
      },
      {
        id: 2,
        content: 'ct2',
      },
      {
        id: 3,
        content: 'ct3',
      },
      {
        id: 4,
        content: 'ct4',
      },
      {
        id: 5,
        content: 'ct5',
      },
    ]);
    const meta = ref<Meta>({
      totalCount: 1200,
    });

    return {
      model: ref(null),
      todos,
      meta,
      options: [
        {
          label: 'Blue',
          value: 'blue',
          description: 'Blue theme',
          icon: 'check_circle',
          color: 'blue',
        },
        {
          label: 'Orange',
          value: 'orange',
          description: 'Orange theme',
          icon: 'check_circle',
          color: 'orange',
        },
      ],
    };
  },
});
</script>
