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


{
"type": "shell",
"inline": [
  "sleep 30",
  "sudo yum update -y",
  "sudo yum install -y puppet"
]
},
 {
   "type": "puppet-masterless",
   "manifest_file": "puppet/manifests/site.pp"
 },

 { "type": "shell",
   "inline": [
     "curl http://169.254.169.254/latest/meta-data/public-ipv4"
   ]
 },
 { "type": "shell-local",
 "command": "egrep -m1 -o '[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}' build.log | xargs -I ip inspec exec linux-baseline -t ssh://ec2-user@ip -i /Users/ricky/.ssh/aminator_kp.pem"
 }

ruby
diff-lcs (< 2.0, >= 1.2.0)
