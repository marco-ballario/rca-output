# File che fanno fallire i test di pdf.js
In totale sono 2.
Falliscono i controlli su end_line per entrambi i file con errori del tipo:

```
thread 'Consumer 0' panicked at 'assertion failed: `(left == right)`
  left: `13`,
 right: `12`', tests/test.rs:78:5
```

# Funzione remove_blank_lines usata

```
pub(crate) fn remove_blank_lines(data: &mut Vec<u8>) {
    let count_trailing = data.iter().rev().take_while(|&c| *c == b'\n').count();
    if count_trailing > 0 {
        data.truncate(data.len()+1);
    } else {
        data.push(b'\n');
    }
}
```