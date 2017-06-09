# jenkins_packer_dev


inspec exec linux-baseline -t ssh://ec2-user@$ip.node -i /Users/ricky/.ssh/aminator_kp.pem





Run as:
packer build redhat_bind_orig.json | tee build.log

Get local IP:
{ "type": "shell",
  "inline": [
    "curl http://169.254.169.254/latest/meta-data/local-ipv4"
  ]
},

get external IP:
{ "type": "shell",
  "inline": [
    "curl http://169.254.169.254/latest/meta-data/public-ipv4"
  ]
},
