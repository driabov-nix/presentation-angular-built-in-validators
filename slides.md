---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS (experimental)
css: unocss
---

# Built-in Validators in Angular

Avoiding cyclic dependency while using them.

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/driabov-nix" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# A little bit about myself

- 🧑‍💻 Working with Angular for 6 years.
- 🤹 Right now am a member of KTC team.
- 🛠 Work a lot with Angular Material source code.
<br>
<br>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# How to use

```ts {all|2-9|10-11|14-21|23-25|all}
@Directive({
  providers: [
    {
      provide: NG_VALIDATORS,
      useExisting: QuantityInputValidator,
      multi: true,
    },
  ],
})
export class QuantityInputValidator
implements Validator {
  private validatorChange = () => {};

  validate(control: AbstractControl<number>) {
    const validator = Validators.compose([
      QuantityValidators.quantity,
      QuantityValidators.min(),
      QuantityValidators.max(),
    ]);
    return validator ? validator(control) : null;
  }

  registerOnValidatorChange(fn: () => void) {
    this.validatorChange = fn;
  }
}
```

---

# When to use

1. When your form control is custom.
2. When validation is always needed for this control.
<br>
<br>

---
layout: iframe
url: https://stackblitz.com/edit/stackblitz-starters-jwqerb
---

# Live Example

---
layout: center
class: text-center
---

# Thank You

[Presentation](https://github.com/driabov-nix/presentation-angular-built-in-validators) · [Live Example](https://stackblitz.com/edit/stackblitz-starters-jwqerb)
