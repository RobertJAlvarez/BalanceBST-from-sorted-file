# BalanceBST from sorted file

1. Implement the following `string.h` library functions:
```c
size_t str_len(const char *s);
int str_n_cmp(const char *s1, const char *s2, size_t n);
int str_cmp(const char *s1, const char *s2);
void *mem_cpy(void *restrict dst, const void *restrict src, size_t n);
char *str_chr(const char *s, int c);
char *str_p_brk(const char *s, const char *charset);
char *str_sep(char **stringp, const char *delim);
char *str_cat(char *s1, const char *s2);
```
3. A tokenizer function in `tokenizer.c` takes two pointers to an array of characters
   which are null terminated and return a null terminated array of characters pointers
   with k not null pointers. k is defined as the number of times when $str[i] = delims[j]$
   where $0 \leq i \lt length(str)$ and $p \leq j \leq length(delims)$.
```c
char **tokenize(char *str, const char *delims)
```
4. A k lines file where each line have the structure “BRAND,MODEL1,MODEL2,…,MODELn\n”
   would be process. Each line in file is order in lexicographic order using "BRAND".
   "BRAND" may be repeated between lines. After the file is process all BRANDS are
   unique (merge all models into a single BRAND line). The following structs and
   functions are created in `process_file.c`:
```c
typedef struct {
 char **lines;
 size_t lines_size;
 size_t n_lines;
} arr_str;
void free_char_pp(char **pp);
size_t read_file(FILE *file, char ***arr_lines);
```
6. Using the process lines, a binary search is apply to make a balance BST. The following
   BST operations are supported in `BST.c`:
```c
typedef struct __node_t {
  char *brand;
  char **models;
  struct __node_t *left_child;
  struct __node_t *right_child;
} node_t;

typedef struct {
  node_t *root;
} bst_t;

void free_bst(bst_t *bst);
int add_line_to_bst(bst_t *bst, char *line);
bst_t *create_bst(FILE *file);
void print_menu(void);
void write_bst(const bst_t *bst, FILE *file);
void print_bst(const bst_t *bst);
int depth(const bst_t *bst);
size_t number_of_nodes(const bst_t *bst);
```
