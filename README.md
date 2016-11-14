## cloudfront_invalidate - A simple ansible module for making Cloudfront invalidation requests

This is a simple Ansible module used to make AWS Cloudfront invalidation requests.  It is designed to be used for tasks such as code deployments where static assets are updated on a Cloudfront distribution and need to have their cache cleared.

### Requirements
* First and foremost, you need Ansible installed and configured for your environment
* python-boto
* The standard EC2 related modules configured for your AWS connection either as environment vars or Ansible vars (or both).

### Installation & Configuration
* Clone/download this repo
* Place the cloudfront_invalidate.py file in your Ansible module path

### Usage
* See the example.yml playbook for a working example (after replacing your details of course)
* Basic usage clearing a single path:
```
- name: "Invalidate a single path"
  cloudfront_invalidate: 
    distribution_id: YOUR_CLOUDFRONT_DIST_ID
    path: "/js/*"
```
* Basic usage clearing a single path:
```
- name: "Invalidate multiple paths"
  cloudfront_invalidate: 
    distribution_id: YOUR_CLOUDFRONT_DIST_ID
    path: "{{ item }}"
  with_items:
    - "/js/*"
    - "/images/*"
```
