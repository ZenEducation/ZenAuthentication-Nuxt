<template>
  <Registration/>
</template>

<script>
import awsconfig from '../src/aws-exports';
import { Amplify, Auth } from "aws-amplify";

Amplify.configure(awsconfig);
export default {
  name: 'IndexPage'
}
</script>
