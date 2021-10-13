<script setup>
import Breadcrumb from '@/components/Breadcrumbs.vue'
const colors = [
  {
    colorName: 'bg-primary text-white',
    theme: 'Primary'
  },
  {
    colorName: 'bg-success text-white',
    theme: 'Success'
  },
  {
    colorName: 'bg-danger text-white',
    theme: 'Danger'
  },
  {
    colorName: 'bg-warning text-white',
    theme: 'Warning'
  },
  {
    colorName: 'bg-info text-white',
    theme: 'Info'
  },
  {
    colorName: 'bg-light text-white',
    theme: 'Light'
  },
  {
    colorName: 'bg-dark text-white',
    theme: 'Dark'
  },
]
const colorsOutlined = [
  {
    colorName: 'border border-primary text-primary hover:bg-primary hover:text-white  ',
    theme: 'Primary'
  },
  {
    colorName: 'border border-success text-success hover:bg-success hover:text-white',
    theme: 'Success'
  },
  {
    colorName: 'border border-danger text-danger hover:bg-danger hover:text-white',
    theme: 'Danger'
  },
  {
    colorName: 'border border-warning text-warning hover:bg-warning hover:text-white',
    theme: 'Warning'
  },
  {
    colorName: 'border border-info text-info hover:bg-info hover:text-white',
    theme: 'Info'
  },
  {
    colorName: 'border border-light text-light hover:bg-light hover:text-white',
    theme: 'Light'
  },
  {
    colorName: 'border border-dark text-dark hover:bg-dark hover:text-white',
    theme: 'Dark'
  },
]
</script>

<template>
  <div class="container mx-auto">
     <Breadcrumb parentTitle='Button' subParentTitle='Buttons' />


    <div class="mt-10">
      <div class="grid md:grid-cols-2 sm:grid-cols-1 gap-4">
        <div>
          <BaseCard>
            <div class="card-title mb-5">Default Buttons</div>
            <BaseBtn 
              v-for="(color, index) in colors"
              :key="index"
              :class="color.colorName" 
              class="mb-3 mr-3"
              
            >
              {{color.theme}}
            </BaseBtn>
          </BaseCard>
        </div>
        <div>
          <BaseCard>
            <div class="card-title mb-5">Outline Buttons</div>
            <BaseBtn 
              v-for="(color, index) in colorsOutlined"
              :class="color.colorName"
              :key="index"
              
              class="mb-3 mr-3"
            >
              {{color.theme}}
            </BaseBtn>
          </BaseCard>
        </div>
        <div>
          <BaseCard>
            <div class="card-title mb-5">Button Block</div>
            <BaseBtn 
              v-for="(color, index) in colors"
              :key="index"
              block
              :class="color.colorName" 
              class="mb-3 mr-3"
            >
              {{color.theme}}
            </BaseBtn>
          </BaseCard>
        </div>
        <div>
          <BaseCard>
            <div class="card-title mb-5">Large & Small Buttons</div>
            <div>
              <BaseBtn 
                v-for="(color, index) in colors"
                :key="index"
                sm
                :class="color.colorName" 
                class="mb-3 mr-3"
              >
                {{color.theme}}
              </BaseBtn>
            </div>
            <div>
              <BaseBtn 
                v-for="(color, index) in colors"
                :key="index"
                :class="color.colorName" 
                class="mb-3 mr-3"
              >
                {{color.theme}}
              </BaseBtn>
            </div>
            <div>
              <BaseBtn 
                v-for="(color, index) in colors"
                :key="index"
                :class="color.colorName" 
                xl
                class="mb-3 mr-3"
              >
                {{color.theme}}
              </BaseBtn>
            </div>
          </BaseCard>
        </div>
        <div>
          <BaseCard>
            <div class="card-title mb-5">Buttons with Icon</div>
            
            <div>
              <BaseBtn 
                
                class="mb-3 mr-3 bg-primary text-white"
              >
                <i class="i-Gear-2"></i>
                
              </BaseBtn>
              <BaseBtn 
                class="mb-3 mr-3 bg-success text-white"
              >
                <i class="i-Gear-2 mr-1"></i>
                Hello World 
              </BaseBtn>
            </div>
          </BaseCard>
        </div>
        
        
      </div>
    </div>
  </div>
</template>
