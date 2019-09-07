---
layout: post
title: "Sam Dela Cruz, Launches Site"
date: 2019-09-06
---

Well. Finally got around to putting this old website together. Neat thing about it - powered by [Jekyll](http://jekyllrb.com) and I can use Markdown to author my posts. It actually is a lot easier than I thought it was going to be.

```typescript
import { Component, forwardRef, Input } from '@angular/core';
import {
  NG_VALUE_ACCESSOR,
  NG_VALIDATORS,
  ControlValueAccessor,
  FormControl,
  Validator
} from '@angular/forms';

const noop = () => {
};

export const CUSTOM_INPUT_CONTROL_VALUE_ACCESSOR: any = {
  provide: NG_VALUE_ACCESSOR,
  useExisting: forwardRef(() => InputJsonComponent),
  multi: true
};

export const CUSTOM_INPUT_CONTROL_VALIDATOR: any = {
  provide: NG_VALIDATORS,
  useExisting: forwardRef(() => InputJsonComponent),
  multi: true
};
```
