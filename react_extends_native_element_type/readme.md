# Introduction

Usually when we are creating a component, we are using a native element like `div`, `span`, `p`, etc...

So if you are creating a Button component, you may use the `onClick` event, right?

So, people create something like this:

```tsx
import React from 'react';

interface ButtonProps {
  onClick: () => void;
  title: string;
}

const Button: React.FC<React.PropsWithChildren<ButtonProps>> = ({ onClick, title }) => {
  return (
    <button onClick={onClick}>
      {title}
    </button>
  );
}
```

But, it's not a good idea to create a interface that has the property `onClick` because it's a native element property.

Remember, ALL native element properties are already in Typescript, you dont need to create it again.

The best way to do this is to extends the native element type.

```tsx

import React from 'react';

interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  title: string;
}

// You can use Type as well, if you are not using custom property
// type ButtonProps = React.ButtonHTMLAttributes<HTMLButtonElement>;

const Button: React.FC<React.PropsWithChildren<ButtonProps>> = ({ onClick, title }) => {
  return (
    <button onClick={onClick}>
      {title}
    </button>
  );
}
```

## Notes

The title can be replaced by children, but i talk about it in another folder.