# ansible-tips
gather_facts: no
tasks:
  - name: Wait for the reboot to complete
    wait_for_connection:
      connect_timeout: 5 # Maximum number of seconds to wait for a connection to happen before closing and retrying.
      sleep: 60 # Number of seconds to sleep between checks
      delay: 180 # Number of seconds to wait before starting to poll.
      timeout: 3600 # Wait up to 1 hour
  
  - name: Wait for server to reboot.
    wait_for:
      host: "{{ ansible_ssh_host }}"
      port: 22
      state: started
    connection: local
    become: no
