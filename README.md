# hello_test_project

2) Reassigning Ownership

REASSIGN OWNED BY ryan TO <newuser>;
Or/and just deleting the object

DROP OWNED BY ryan;
3) Executing REVOKE PRIVILEGES

REVOKE ALL PRIVILEGES ON ALL TABLES IN SCHEMA public FROM ryan;
REVOKE ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public FROM ryan;
REVOKE ALL PRIVILEGES ON ALL FUNCTIONS IN SCHEMA public FROM ryan;
4) Dropping the user
DROP USER ryan;

REASSIGN OWNED BY  class_of_ntek TO postgres;
DROP OWNED BY class_of_ntek;
DROP ROLE class_of_ntek;

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

- name: installing updated packages
  yum:
    security: yes
    name: '*'
    state: present
    exclude: kernel*
  register: patch_linux_updated
