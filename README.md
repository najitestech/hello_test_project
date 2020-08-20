# hello_test_project

- name: Copy the file from master to the destination
  shell: pwd
  register: pwd

- name: set facts
  shell: whoami
  register: user
  
- name: Make a new folder
  file:
    path: /AWX-FOLDER
    mode: 0755
    state: absent
  
- name: Debugging outputs
  debug:
    var: "{{ item }}"
  with_items:
    - pwd.stdout_lines
    - user.stdout_lines
