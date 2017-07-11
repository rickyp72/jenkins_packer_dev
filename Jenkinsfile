#!groovy

node {
  branch=env.ghphTargetBranch ? env.ghphTargetBranch : env.BRANCE_NAME
  def err = null
  currentBuild.result = "SUCCESS"

  try {
    stage 'Checkout'
      checkout scm

    stage 'Validate'
<<<<<<< HEAD
      def packer_file = 'ova_creater_new.json'
=======
      def packer_file = 'packer_duel_inspec_rhel_jenk.json'
>>>>>>> 7fb4770465e7eb271b105676df6c832e42dede3b
      print "Running packer validate on : ${packer_file}"
      sh "packer -v ; packer validate ${packer_file}"

    stage 'Build'
      sh "packer build ${packer_file} | tee build.log"

    stage 'Test'
      print "Testing goes here."
  }

  catch (caughtError) {
    err = caughtError
    currentBuild.result = "FAILURE"
  }

  finally {
    /* Must re-throw exception to propagate error */
    if (err) {
      throw err
    }
  }
}
