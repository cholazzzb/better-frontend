```tsx
import { useForm } from "react-hook-form";
import { useLens } from "@hookform/lenses";

import { InputText } from "./InputText";

type FormValues = {
  account: {
    profile: {
      username: string;
      email: string;
    };
  };
};

const defaultValues: FormValues = {
  account: {
    profile: {
      username: "",
      email: "",
    },
  },
};

export function AppForm() {
  const { control } = useForm<FormValues>({
    defaultValues,
  });

  const baseLens = useLens({ control });

  const profileLens = baseLens.focus("account").focus("profile");

  return (
    <InputText
      label="Username"
      lens={profileLens.focus("username")}
      placeholder="Enter your username"
    />
  );
}
```
