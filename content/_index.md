---
date: "2023-04-12"
sections:

- block: about.avatar
  content:
    text: null
    username: admin
  id: about

- block: features
  id: skills-1
  content:
    title: Habilidades requeridas
    items:
    - description: 90%
      icon: r-project
      icon_pack: fab
      name: R
    - description: 100%
      icon: chart-line
      icon_pack: fas
      name: Estatística
    - description: 10%
      icon: python
      icon_pack: fab
      name: Python



- block: portfolio
  id: aulas
  content:
    title: Aulas
    filters:
    # Folders to display content from
      folders:
        - slides
        # Only show content with these tags
      tags: []
        # Exclude content with these tags
    sort_by: 'Date'
    sort_ascending: true
      # Default portfolio filter button
      # 0 corresponds to the first button below and so on
      # For example, 0 will default to showing all content as the first button below shows content with *any* tag
    default_button_index: 0
      # Filter button toolbar (optional).
      # Add or remove as many buttons as you like.
      # To show all content, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the button toolbar, delete the entire `buttons` block.
    buttons:
      - name: Todas
        tag: '*'
      - name: Conceitos Iniciais
        tag: Conceitos
      - name: Pré-processamento
        tag: Pre
      - name: Classificação
        tag: Classificação
  design:
      # See Page Builder docs for all section customization options.
      # Choose how many columns the section has. Valid values: '1' or '2'.
    columns: '2'
      # Choose a listing view
    view: Card
      # For Showcase view, flip alternate rows?
    flip_alt_rows: false


- block: portfolio
  id: scripts
  content:
    title: Scripts
    filters:
    # Folders to display content from
      folders:
        - scripts
        # Only show content with these tags
      tags: []
        # Exclude content with these tags
    sort_by: 'Date'
    sort_ascending: false
      # Default portfolio filter button
      # 0 corresponds to the first button below and so on
      # For example, 0 will default to showing all content as the first button below shows content with *any* tag
    default_button_index: 0
      # Filter button toolbar (optional).
      # Add or remove as many buttons as you like.
      # To show all content, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the button toolbar, delete the entire `buttons` block.
    buttons:
      - name: Todas
        tag: '*'
      - name: Pré-processamento
        tag: Pre
  design:
      # See Page Builder docs for all section customization options.
      # Choose how many columns the section has. Valid values: '1' or '2'.
    columns: '2'
      # Choose a listing view
    view: Card
      # For Showcase view, flip alternate rows?
    flip_alt_rows: false





  
- block: portfolio
  content:
    buttons:
    - name: Todos
      tag: '*'
    - name: Classificação
      tag: Classificação
    default_button_index: 0
    filters:
      folders:
      - project
    title: Projetos
  design:
    columns: "2"
    flip_alt_rows: false
    view: Card
  id: projects
  
  
  
  

  
  
  
  
- block: collection
  content:
    count: 5
    filters:
      author: ""
      category: ""
      exclude_featured: false
      exclude_future: false
      exclude_past: false
      folders:
      - post
      publication_type: ""
      tag: ""
    offset: 0
    order: desc
    subtitle: ""
    text: ""
    title: Posts recentes
  design:
    columns: "2"
    view: compact
  id: posts



title: null
type: landing
---
