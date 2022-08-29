# TheoremParts: Documentation

## Usage

### `EnumerateClaims` environment

Provides a special numbered list which can be used inside theorem-like environments for enumerating claims.

#### Example
```latex
\begin{proposition}
  For any real numbers $a$, $b$ and $c$, we have:
  \begin{EnumerateClaims}
    \item\label{Commutativity} $a + b = b + a$.
    \item\label{Associativity} $(a + b) + c = a + (b + c)$.
  \end{EnumerateClaims}
\end{proposition}
```

#### Notes

- The default (global) reference, obtained by `\ref` or `\cref` commands (if `cleveref` package is loaded), contains
  both the number of the theorem-like environment enclosing the claim and the number of the claim itself. For
  instance, if the `proposition` in the example above has number 3, then `\ref{Associativity}`
  and `\cref{Associativity}` produce `3(ii)` and `proposition 3(ii)`, respectively.

- Sometimes (for example, in the proof) it might be useful to obtain the simple (local) reference, containing just the
  claim number. For this, use the dedicated `\LocalClaimReference` command.

- In principle, the `EnumerateClaims` environment can be used even outside theorem-like environments. In this case, it
  simply produces a specially formatted enumerated list but does not modify any references (thus, `\ref` and `\cref`
  commands act as they usually do for the standard `enumerate` list). However, the real power of the `EnumerateClaims`
  environment comes from the referencing mechanism described above. By default, this mechanism is activated only inside
  the following theorem-like environments:
    - `theorem`
    - `lemma`
    - `proposition`

  If you want to add a new environment to this list, such as `remark`, you can use the following command in the
  preamble:
  ```latex
  \EnumerateClaimsActivateInside{remark}
  ```
  Use this command several times if there are several such environments.

### `\ProofPart` command

Marks the beginning of the new part inside the `proof` environment. Useful for
splitting a long proof into several parts.

## Examples

See [this LaTeX source file](Example/src/Main.tex).