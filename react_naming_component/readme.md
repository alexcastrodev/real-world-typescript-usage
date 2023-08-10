# Introduction

Maybe you dont need to use `React.FC` to create a component.

# The problem example

You can use export default function or export default class.

The common way to create a component is:

```tsx

import React from 'react';

type ButtonProps = React.ButtonHTMLAttributes<HTMLButtonElement>

const ButtonExampleA: React.FC<React.PropsWithChildren<ButtonProps>> = ({ children }) => {
  return (
    <button {...props}>
      {children}
    </button>
  );
}
```



# The solution example

The best way to do this is to extends the native element type.

```tsx

import React from 'react';

type ButtonProps = React.ButtonHTMLAttributes<HTMLButtonElement>

const ButtonExampleA: React.FC<React.PropsWithChildren<ButtonProps>> = ({ children }) => {
    return (
      <button {...props}>
        {children}
      </button>
    );
}

// OR

export default function ButtonExampleB({ children }: React.PropsWithChildren<ButtonProps>) {
  return (
    <button>{children}</button>
  )
}

// OR

export default class ButtonExampleC extends React.Component<ButtonProps> {
  render() {
    return (
      <button>{this.props.children}</button>
    )
  }
}
```

# Conclusion

You can use `React.FC` to create a component, but you dont need to use it.
